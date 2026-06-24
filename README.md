## Community Choice and Reasoning
The community that I chose is the r/PlantClinic subreddit. r/PlantClinic is a community where plant owners seek help diagnosing and solving plant health issues. I chose this community, because I enjoy gardening in my free time and I frequently search for advice for my plants' issues online. This community is a great fit for a classification task, because the threads are focussed on a variety of plant issues. Users offer diagnoses, background information on specific plants, recommendations, and even personal anecdotes about their own plants. The varied discourse makes this subreddit well suited for a classification task.

## Label taxonomy: definitions and 2 examples per label

**Label Definitions**
Information Seeking - A comment whose primary purpose is to request additional information needed to understand, diagnose, or evaluate a plant-related issue. 
    Example 1: "How often are you watering it?"
    Example 2: "How long has it been in that pot? And does the container have drainage holes?"

Explanation - A comment whose primary purpose is to help the reader understand a cause, mechanism, symptom, or aspect of plant behavior.
    Example 1: "Spider plants are sensitive to fluoride and chlorine, which can cause brown leaf tips."
    Example 2: "The white residue is most likely mineral buildup from hard water. As the water evaporates, dissolved minerals are left behind on the soil surface and pot."

Recommendation - A comment whose primary purpose is to persuade the reader to take a specific action, even when explanation or personal experience is provided as supporting evidence. 
    Example 1: "Repot it into a chunkier soil mix and reduce watering."
    Example 2: "I'd move it to a brighter window and cut back on watering for a few weeks. Let the soil dry out almost completely before watering again."

Experience Sharing - A comment whose primary purpose is to describe the commenter's own plant-care experiences, observations, or outcomes. 
    Example 1: "I had the same issue with my aloe, and it recovered after I repotted it."
    Example 2: "My fiddle leaf fig did the same thing last winter. Once I moved it away from the heating vent and increased the humidity, it started putting out healthy new leaves again."

**Decision Rules and Tie-breakers**
--Decision Rules--
1. If a comment asks for additional information needed to understand, diagnose, or evaluate a plant-related issue, classify it as information_seeking, even if it also contains a tentative diagnosis or recommendation.

2. Label as explanation when the primary goal is helping the reader understand a cause, mechanism, symptom, or plant behavior.

3. Label as recommendation when the primary goal is persuading the reader to take a specific action, even if explanation or personal experience is used as supporting evidence.

4. Label as experience_sharing when the comment primarily describes the commenter's own plant, routine, observation, or outcome.

--Tie-breakers--
1. If explanation is primarily used to justify or support a recommended action, choose recommendation.
2. If personal experience is primarily used to justify or support a recommendation, choose recommendation.
3. If personal experience is primarily used to illustrate or support a broader explanation, choose explanation.

## Data Collection Source, Labeling Process and Label Distribution, and Examples of Difficult to Label Cases

**Data Collection Source**
I collected the comments from the following r/PlantClinic subreddit threads:

|Title| Link|
|New to plant life. Seeking help!| https://www.reddit.com/r/plantclinic/comments/1ubvt9j/new_to_plant_life_seeking_help/|
|Help! Does anybody know what's causing this gray thing in my tree?| https://www.reddit.com/r/plantclinic/comments/1uc1gmj/so_many_lil_worms_are_they_harmful_or_helpers/|
|Did my succulents die overnight?| https://www.reddit.com/r/plantclinic/comments/1ublkjf/did_my_succulents_die_overnight/|
|Assistance needed with Bird of Paradise| https://www.reddit.com/r/plantclinic/comments/1ubzpyq/assistance_needed_with_bird_of_paradise/|
|Why did little bloom die?| https://www.reddit.com/r/plantclinic/comments/1u6zzds/why_did_little_bloom_die/|
|Why are my pothos leaves turning yellow? I watered them 28 days ago.| https://www.reddit.com/r/plantclinic/comments/1ucj7xr/why_are_my_pothos_leaves_turning_yellow_i_watered/|
|Anyone know the remedy to this on my corn plant?| https://www.reddit.com/r/plantclinic/comments/1ucudp2/anyone_know_the_remedy_to_this_on_my_corn_plant/|
|what am i doing wrong here?| https://www.reddit.com/r/plantclinic/comments/1uchzns/what_am_i_doing_wrong_here/|
|Sentimental draceana help!| https://www.reddit.com/r/plantclinic/comments/1ud3cbx/sentimental_draceana_help/|
|What is happening??| https://www.reddit.com/r/plantclinic/comments/1ucn7mj/what_is_happening/|
|Blackberry plant dying back considerably after transplant| https://www.reddit.com/r/plantclinic/comments/1ucvbi5/blackberry_plant_dying_back_considerably_after/|
|Rubber Tree Leaf Drop| https://www.reddit.com/r/plantclinic/comments/1uccauo/rubber_tree_leaf_drop/|
|Scale on plant, how to rid?| https://www.reddit.com/r/plantclinic/comments/1ud24ls/scale_on_plant_how_to_rid/|
|Kalanchoe is drooping after re-potting| https://www.reddit.com/r/plantclinic/comments/1ud07lu/kalanchoe_is_drooping_after_repotting/|
|plant not recovering from repotting| https://www.reddit.com/r/plantclinic/comments/1uczlo2/plant_not_recovering_from_repotting/|
|What can i do to keep my cat away from the plant.| https://www.reddit.com/r/plantclinic/comments/pkhcuv/what_can_i_do_to_keep_my_cat_away_from_the_plant/|
|Indoor oxalis vs outdoor oxalis experiment - I guess I'll be letting them live outside then| https://www.reddit.com/r/plantclinic/comments/grc4ds/indoor_oxalis_vs_outdoor_oxalis_experiment_i/|

**Preprocessing Decisions**
During data collection, I manually copied comments from the Reddit threads to a csv file. While collecting comments, I made several preprocessing decisions to improve label quality and consistency. I selected only top-level comments and excluded replies, to ensure that the content focused on direct responces to the original poster. I excluded comments such as jokes, responses containing only emojis, and other low-information comments. 

**Labeling Process**
I manually labeled the comments using the taxonomy described above and the additional decision rules and tie-breakers that I developed to handle ambiguous cases where comments contained multiple discourse functions. I also made sure that I sampled comments from multiple thread types to better represent the range of discussions found in r/PlantClinic and in order to avoid overrepresenting any single conversation.

**Label Distribution**
The dataset contains 200 labeled comments.  The label distribution is as follows:

|Label| Count| Percentage|
|Recommendation| 81| 40.5%|
|Explanation| 48| 24.0%|
|Information Seeking| 37| 18.5%|
|Experience Sharing| 34| 17.0%|

The label distribution is modoerately imbalanced, with the Recommendation label representing 40.5% of the total labeled comments. However, I believe this is a reflection of the Reddit community's stated purpose, which is to provide plant-care advice and recommendations. Due to the classes not being perfectly balanced, my evaluation also considers macro-averaged precision, recall, and F1 score in addition to overall accuracy.

**Examples of Difficult to Label Cases**

--Example 1--

"Spider plants are very sensitive to fluoride and chlorine in tap water. Over time, minerals build up in the soil and cause the leaf tips to turn brown. You should switch to distilled water and flush the soil every few weeks."

Why this is Difficult: The first two sentences would be considered Explanation, because they aim to help the reader understand the cause of the browning plant tips.  The last sentence is a direct recommendation.

Final Label: Recommendation

Reason: The explanation provided in the comment is being used to convince the reader to water their plant with distilled water rather than tap water. I applied tie breaker #1 to reach this conclusion.

--Example 2--

"I had this exact problem with my aloe last year. I stopped watering it for about two months and moved it into brighter light, and it eventually recovered."

Why this is Difficult: Here, the commenter speaks only about their experience with their aloe plant, however, it's clear that their intent is for the reader to infer the recommendation from their story.

Final Label: Experience Sharing

Reason: Here, I referred to decision rule # 4. Regardless of the intent, because this comment only speaks about the writer's plants/experience, it is labeled as Experience Sharing.

--Example 3--

"Try letting the soil dry out completely before watering again. How often are you watering it?"

Why this is Difficult: The comment above contains both a recommendation and a clarifying question directed at the original poster.  Therefore, it contains parts that could be labeled Recommendation or as Information Seeking.

Final Label: Information Seeking

Reason: I referenced decision rule #1 listed above. Even if the comment gives an explanation or recommendation, the fact that the commenter also asks for additional information implies that their explanation/recommendation was tentative/preliminary, because they didn't have all the information that they needed to provide tailored advice.  Therefore, the final label is Information Seeking.

## Fine-tuning approach:

**Base Model**
DistilBERT with a classification head

**Training Setup and Hyperparameter Decisions**
My dataset contains 200 total examples.  The examples were split thusly:
Training Set: 140 examples
Validation Set: 30 examples
Test Set: 30 examples

Relatively speaking, 140 examples is considered a small training set. I adjusted the hyperparameters in an attempt to make up for the small training set.

I increased the number of training epochs from 3 to 5. With only 140 examples, the model sees relatively little data during each pass through the training set. Adding additional epochs gives the model more opportunities ot learn the differences between the labels.

I reduced the learning rate from 2e-5 to 1e-5. Due to the small size of the training set, a lower learning rate can help keep the model from making large parameter updates that end up overfitting to a particular class, pattern, etc. in the training data.

I reduced the warmup steps from 50 to 0. Using the default hyperparameters that came with the assignment template, if I have 140 training examples and a batch size of 16, number of training steps per epoch would be 140 / 16 = 8.75, which is roughly 9. If we only have 3 epochs, then we only have 9 x 3 training steps accross the entire run. Originally, the number of warmup steps was set to 50, which is longer than the number of training steps, 27.This could lead to the model spending the entire training run in the warmup phase and never fully reaching the intended learning rate.


## Baseline Description
**Baseline Model**
Groq's llama-3.3-70b-versatile

**Prompt Used**
You are classifying comments from r/plantclinic, a Reddit community that helps users diagnose and treat problems with their plants.
Assign each comment to exactly one of the following categories.

information_seeking: A comment whose primary purpose is to request additional information needed to understand, diagnose, or evaluate a plant-related issue.
Example: "How long has it been in that pot? And does the container have drainage holes?"

explanation: A comment whose primary purpose is to help the reader understand a cause, mechanism, symptom, or aspect of plant behavior.
Example: "The white residue is most likely mineral buildup from hard water. As the water evaporates, dissolved minerals are left behind on the soil surface and pot."

recommendation: A comment whose primary purpose is to persuade the reader to take a specific action, even when explanation or personal experience is provided as supporting evidence.
Example: "I'd move it to a brighter window and cut back on watering for a few weeks. Let the soil dry out almost completely before watering again."

experience_sharing: A comment whose primary purpose is to describe the commenter's own plant-care experiences, observations, or outcomes.
Example: "My fiddle leaf fig did the same thing last winter. Once I moved it away from the heating vent and increased the humidity, it started putting out healthy new leaves again."


Decision rules:

1. If a comment asks for additional information needed to understand, diagnose, or evaluate a plant-related issue, classify it as information_seeking, even if it also contains a tentative diagnosis or recommendation.

2. Label as explanation when the primary goal is helping the reader understand a cause, mechanism, symptom, or plant behavior.

3. Label as recommendation when the primary goal is persuading the reader to take a specific action, even if explanation or personal experience is used as supporting evidence.

4. Label as experience_sharing when the comment primarily describes the commenter's own plant, routine, observation, or outcome.

Tie-breakers:

- If explanation is primarily used to justify or support a recommended action, choose recommendation.

- If personal experience is primarily used to justify or support a recommendation, choose recommendation.

- If personal experience is primarily used to illustrate or support a broader explanation, choose explanation.


Respond with ONLY the label name.
Do not explain your reasoning.

Valid labels:
information_seeking
explanation
recommendation
experience_sharing

**How Results Were Collected**

I gave the baseline model a prompt containing the community description, label definitions, one example for each label, and annotation decision rules. For each test comment, the model was instructed to return exactly one of the four label names. The predictions were compared against the ground-truth labels that I labeled myself in the held-out test set. Accuracy, precision, recall, and F1 scores were then computed from these predictions.

## Evaluation Report

**Overall Accuracy**
Baseline: 86.7%
Fine-Tuned DistilBERT: 40.0%

The prompt-based baseline substantially outperformed the fine-tuned model. While the baseline achieved strong performance across all four labels, the fine-tuned model largely collapsed to predicting the Recommendation class.

**Per-Class Metrics**

Baseline Model
| Label | Precision | Recall | F1 |
| Information Seeking | 1.00| 0.67 | 0.80 |
| Explanation | 0.86 | 0.86	| 0.86 |
| Recommendation | 0.86 | 1.00 | 0.92 |
| Experience Sharing | 1.00 | 1.00 | 1.00 |
| Macro Average | 0.93 | 0.88 | 0.90 |

Fine-Tuned Model
| Label	Precision| Recall| F1 |
| Information Seeking | 0.00 | 0.00 | 0.00 |
| Explanation| 0.00 | 0.00 | 0.00 |
| Recommendation| 0.40 | 1.00 | 0.57 |
| Experience Sharing | 0.00 | 0.00 | 0.00 | 
| Macro Average | 0.10 | 0.25 | 0.14 |

Confusion Matrix (Fine-Tuned Model)
| True Label| Information Seeking| Explanation| Recommendation | Experience Sharing |
| Information Seeking | 0 | 0 | 6 | 0 |
| Explanation | 0 | 0 | 7 | 0 |
| Recommendation | 0 | 0 | 12 | 0 |
| Experience Sharing | 0 | 0 | 5 | 0 |

The confusion matrix shows that the model predicted Recommendation for every test example. All Information Seeking, Explanation, and Experience Sharing comments were misclassified as Recommendation.

**Error Analysis**

Comment: "How many times should we water them?"
True Label: Information Seeking
Predicted Label: Recommendation
Analysis: This comment is a direct request for information. The model appears to have ignored the question format and instead associated the topic of watering with Recommendation comments seen during training.


Comment: "Looks to be overwatered."
True Label: Explanation
Predicted Label: Recommendation
Analysis: This comment provides a diagnosis and explanation of the plant's condition. The model incorrectly treated it as advice, suggesting that it failed to learn the distinction between identifying a problem and recommending a solution.


Comment: "This is one of my favorite plants in my collection! He's somehow healthy inside. I'm in the process of rearranging my entire bedroom to make more space to get more plants in better sun."
True Label: Experience Sharing
Predicted Label: Recommendation
Analysis: The comment primarily describes the author's personal experience and observations. The model appears to have focused on phrases related to plant care and sunlight rather than the communicative purpose of the comment.

**Sample Classifications**

| Comment (Excerpt) | Predicted Label | Confidence | Correct? |
| "Looks to be overwatered." | Recommendation | 0.29 | No |
| "How many times should we water them?" | Recommendation | 0.32 | No |
| "This is one of my favorite plants in my collection..." | Recommendation | 0.32 | No |
| "Too much water. Stop watering it for at least 3 months..." | Recommendation | 0.36 | Yes |
| "Get plants for your cat. I have 2 boxes I rotate through..." | Recommendation | 0.36 | No |

**Example of a Correct Prediction**

"Too much water. Stop watering it for at least 3 months and see if it improves."

The model correctly classified this comment as Recommendation because the primary communicative intent is to tell the reader what action to take. Although the comment includes an explanation of the problem, the explanation is used to support the recommendation, which matches the annotation guidelines used during labeling.

## Reflection

My goal was for the classifier to be able to classify comments from r/PlantClinic into four categories that would be useful to users: Information Seeking, Explanation, Recommendation, and Experience Sharing. During annotation, I put a lot of time into developing detailed label definitions and tie-breaker rules to separate comments that combined multiple functions.

The prompt-based baseline model was largely able to pick up on these distinctions. The prompt it was given contained explicit definitions, examples, and annotation guidelines.  Due to this, it was able to reason about the communicative intent of each comment rather than relying solely on keywords.

The fine-tuned DistilBERT model learned a much simpler decision boundary than intended. Instead of distinguishing among the four discourse functions, it appears to have learned that this community's discussions are very often recommendations. Therefore, it predicted Recommendation for nearly every example. This suggests that the model overfit to the most common class in the training data rather than learning the differences between asking questions, explaining causes, sharing experiences, and providing advice.


## Spec Reflection
Preparing the spec was very helpful in helping me to update my label definitions and particularly helpful in helping me to develop the additional decision rules and tie breakers.  As I sampled comments from my chosen Reddit community, I discovered that comments frequently contained material that could warrent multiple labels. I kept track of these and how I resolved them in my spec, then used these to develop the additional set of decision rules to help labeling with ambiguous comments.

One place that my implementation diverged from the spec was in my use of AI. Initially, I had planned to use AI to scrape the comments from Reddit, but I ended up manually copying the comments to a csv file myself. This allowed me to become more in tune with the different thread types in r/PlantClinic, which consequently led to different types of comments. For example some threads were looking for advice, some threads were giving updates on certain plants. This helped me choose a variety of thread types so that there was more diversity in the comments included in my dataset.

## AI Usage
As I worked through some initial labeling examples, I came accross multiple comments that contained content that could warrent multiple labels. As I came accross these cases, I used ChatGPT to help finetune my logic for why I was designating a specific label tasked ChatGPT with turning these decisions into as set of decision rules.  One think that I revised was that originally, ChatGPT recommended marking comments that had a recommendation and a question in it as Recommendation. I revised this though, as I noticed that posts that give recommendations and then ask clarifying questions are usually giving tentative advice based on general information, but then seek clarifcation from the original poster in order to make more directed or relevant recommendations.  Considering the tentative nature of the recommendations in these posts, I chose to label these kinds of comments as Information Seeking. 

I ran the fine tuned model once with the default hyperparameters and ended up getting a surprisingly low overall accuracy score. I asked ChatGPT to explain the current hyperparameters for DistilBERT and to make recommendations for changes. The AI suggested several modifications, including changing the learning rate and warmup steps. After testing these changes, I analyzed the results myself and concluded that the model continued to collapse to the majority class, leading me to focus my discussion on the limitations of fine-tuning with a small dataset rather than assuming the modifications had improved performance.