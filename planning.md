## Community
The community that I chose is the r/PlantClinic subreddit. r/PlantClinic is a community where plant owners seek help diagnosing and solving plant health issues. I chose this community, because I enjoy gardening in my free time and I frequently search for advice for my plants' issues online. This community is a great fit for a classification task, because the threads are focussed on a variety of plant issues. Users offer diagnoses, background information on specific plants, recommendations, and even personal anecdotes about their own plants. The varied discourse makes this subreddit well suited for a classification task.

## Labels
**Design Choices**
I classify comments into Information Seeking, Explanation, Recommendation, and Experience Sharing because these represent the primary ways community members contribute to discussions: gathering missing information, explaining plant problems, suggesting solutions, and sharing relevant personal experiences. These distinctions matter because each type of comment plays a different role in helping users understand and address issues with their plants.

**Label Definitions**
Information Seeking - A comment whose primary purpose is to request additional information needed to understand, diagnose, or evaluate a plant-related issue. Ex: "How often are you watering it?"

Explanation - A comment whose primary purpose is to help the reader understand a cause, mechanism, symptom, or aspect of plant behavior. Ex: "Spider plants are sensitive to fluoride and chlorine, which can cause brown leaf tips."

Recommendation - A comment whose primary purpose is to persuade the reader to take a specific action, even when explanation or personal experience is provided as supporting evidence. Ex: "Repot it into a chunkier soil mix and reduce watering."

Experience Sharing - A comment whose primary purpose is to describe the commenter's own plant-care experiences, observations, or outcomes. Ex: "I had the same issue with my aloe, and it recovered after I repotted it."

**Decision Rules**
    Information Seeking
        If a comment asks for additional information needed to evaluate the situation, classify it as Information Seeking, even if it contains a preliminary observation or recommendation.
    Explanation vs. Recommendation
        Label as Explanation when the primary goal is helping the reader understand a cause, mechanism, symptom, or plant behavior.
        Label as Recommendation when the primary goal is persuading the reader to take a specific action, even if explanation or personal experience is used as supporting evidence.
        If a comment contains both Explanation and Recommendation, and the explanation primarily serves to support, justify, or persuade the reader to take an action, label it as Recommendation.
    Experience Sharing vs. Recommendation
        Label as Experience Sharing when the comment primarily describes the commenter's own plant, care routine, observations, or outcomes, even if the reader could infer advice from it.
        Label as Recommendation when the commenter directly tells the original poster what to do.
    Short Action-Oriented Comments
        Short direct fixes, commands, or action phrases are labeled Recommendation, even when they are very brief.
        Ex:
            "Distilled water."
            "Scissors."
            "Move it away from the heater."

# Hard Edge Cases

**Explanation vs. Recommendation**
A common pattern when responding to threads is to first give a diagnosis, which in my taxonomy would fall under Explanation, and then give advice to solve the problem, which under this taxonomy would fall under Recommendation.  Here's an example:

"Spider plants are very sensitive to fluoride and chlorine in tap water. Over time, minerals build up in the soil and cause the leaf tips to turn brown. You should switch to distilled water and flush the soil every few weeks."

The first two sentences would be considered Explanation, because they aim to help the reader understand the cause of the browning plant tips.  The last sentence is a direct recommendation.

I will solve this by using the Explanation vs. Recommendation decision rule described above.  Since the explanation provided in the comment is being used to convince the reader to water their plant with distilled water rather than tap water, this comment would be labeled a Recommendation.

**Experience Sharing vs. Recommendation**
Another common pattern in this subreddit is to answer the original poster's question by writing about one's own experience and not giving explicit recommendaitons, but the recommendaiton is meant to be inferred from the experience/anecdote.  Here's an example comment:

"I had this exact problem with my aloe last year. I stopped watering it for about two months and moved it into brighter light, and it eventually recovered."

Here, the commenter speaks only about their experience with their aloe plant, however, the intent is for the reader to infer the recommendation from their story.

I will solve cases like this using the Experience Sharing vs. Recommendation decision rule described above. The rule says to label the comment as Experience Sharing if the comment primarily describes the commenter's own plant, care routine, observations, or outcomes, even if the reader could infer advice from it.

**Information Seeking vs. Recommendation**
Another pattern that I came accross in the subreddit that the commenter might offer a tentative explanation or recommendation, but also asks a clarifying question about the original poster's issue.  Here is an example:

"Try letting the soil dry out completely before watering again. How often are you watering it?"

These cases will be decided by the Information Seeking decision rule described above. Even if the comment gives an explanation or recommendation, the fact that the commenter also asks for additional information implies that their explanation/recommendation was tentative/preliminary, because they didn't have all the information that they needed to provide tailored advice.  In these cases, I will label the comment as Information Seeking.

# Data Collection Plan
I will collect examples from the r/PlantClinic subreddit using Python's Reddit API Wrapper (PRAW). In the sample set of comments that I reviewed to design my system's labels, I found that the distribution of labels was:
Information Seeking - 8%
Explanation - 46%
Recommendation - 31%
Experience Sharing - 15%

Therefore, for 200 examples, I will expect approximately the following number of comments per label:
Information Seeking - 16
Explanation - 92
Recommendation - 62
Experience Sharing - 30

Due to the label distribution that I have already seen in the example set, I am already expecting some labels to have less occurrences than others (ex. Information Seeking).  However, if any label becomes underrepresented in the initial 200 comments, I will intentionally collect additional examples that fit the label until the distribution is more balanced.

# Evaluation Metrics
I will evaluate my model using overall accuracy and per class precision, recall, and F1 scores.
Accuraccy measures how often the model correctly labels a comment, but this by itself isn't sufficient, because the label distribution might not be perfectly balanced.  For example, let's say it's accuraccy is 75% overall, but the 25% it is getting wrong are all from one class. This would mean it is not correctly labeling an entire class, adn therefore, I wouldn't consider the model successful.

This is why I also added per class precision, recall, and F1 scores. Precision measures how often the model's predictions for a label are correct. Recall measures how often the model succcessfully identifies examples that truly belong to that label. The F1 score combines and balances precision and recall and is particularly useful for comparing performance across labels that may have different frequencies.

# Definition of Success
I would consider this classifier successful if:
    1. It significantly outperforms the zero-shot Llama 3.3 baseline.
    2. Achieves an overall accuracy of at least 75% on the test set.
    3. Achieves an F1 score of at least 0.70 for each label, indicating that the model can reliably distinguish between labels.
For use as a community tool, I would consider the classifier "good enough" if it can correctly identify the primary communicative function of a comment most of the time and maintain consistent performance across all four labels. Differentiating between Explanation and Recommendation will likely be the trickiest, since these are the most similar categories in my taxonomy. However, even if some ambiguous comments are misclassified, the classifier would still be useful if it provides a reasonably accurate summary of how users contribute to discussions and if the majority of errors occur on genuinely borderline cases rather than clear-cut examples.

# AI Tool Plan
**Script for Pulling Data**
I will use ChatGPT to assist with creating a script that calls the Reddit's API to scrape the threads/comments from r/PlantClinic and load them into a CSV file.  I will give it the Data Collection Plan section of my planning doc.

**Label Stress-testing/Decision Rules:**
While deciding on the community and sampling comments from a few sample threads, I asked ChatGPT to assist with creating decision rules for edge cases that I came across. For example, I came across comments that had aspects from multiple labels. ChatGPT helped me create decision rules that help clearly distinguish between categories. I confirmed that the decision rules are correct by finding additional comments that were edge cases and labeling them myself, according to the decision rules that we agreed upon.

**Failure Analysis:**
I plan to give ChatGPT my list of wrong predictions and I will ask it to identify patterns before I write my evaluation report. I will double check any patterns that it suggests by examining the incorrect predictions to see if they fit the pattern. If a particular class comes back with a low F1 score, I will examine the incorrect predictions for that particular class, my label definitions, and my decision rules, and try to find a pattern as to why that class is being mislabeled.