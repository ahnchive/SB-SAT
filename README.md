# Stony Brook SAT reading fixation dataset (SB-SAT)
Additional details about the eyetracking data and models can be found in this [paper](https://dl.acm.org/doi/abs/10.1145/3379156.3391335).


# Repo structure

There are three folders in this repo:
- `stimuli` contains the screenshots of four reading passages and questions used in the task
- `model` contains the preprocessed fixation dataset used for model training (with different types of data splits, please see the main paper for details). We also include the sample colab [code](https://github.com/ahnchive/SB-SAT/blob/master/model/model_training.ipynb) for training models for comprehension prediction.
- `fixation` contains the raw eye-movemenet data in csv. See below for more detailed description on the reported variables.


# Variables in fixation dataset:

## raw fixation dataset 
`18sat_fixfinal.csv` contains raw eyemovement measures recorded using Eyelink 1000 (1000hz sampling rate). This file also contains which word of the passage the current gaze is fixated on (`CURRENT_FIX_INTEREST_AREA_LABEL` column). We exported all eye-movement measures using SR Research Eyelink Data Viewer program. You can see the detailed description about each eye-movement measure in their [manual](https://www.sr-research.com/support/attachment.php?aid=663). `18sat_trialfinal.csv` contains eye-movment measures are averaged or aggreaged for each trial (each page). Additional details about the other variables:

- RECORDING_SESSION_LABEL: subject id
- INDEX: trial id
- type: whether this trial belongs to reading or question
- book_name: reading passage name id
- book:	reading passage integer id
- page: current page number for each reading passage
- total_page: total page number for each reading passage
- RT: total reading time for each page
- answer: subject's key response
- correct_answer: correct response (no correct reponse for reading trials, replaced as -99)
- page_name: the filename used for image stimuli (in stimuli folder)


## question response 
`18sat_labels.csv` has subject demographics and preprocessed question responses for model training (see paper for details how we preprocess this data)

- subj: subject id
- language: native langauge
- native: whether native langauge is english (0-no, 1-yes)
- book: reading passage id
- acc: average passage accuracy
- acc_level: average passage accuracy level in quartile (0: lowest 25%, 1: 25-50%, 2: 50-75%, 3: highest 25%)
- subj_acc: individual’s comprehension score averaged over all four passages 
- subj_acc_level: subj_acc level in quartile (0: lowest 25%, 1: 25-50%, 2: 50-75%, 3: highest 25%)
- other variables; subject's subjective evaluation on their cognitive and mental states while reading this passage (default is higher the number, higher the state, number range from 0 to 3)
  - confidence: How confident were you when answering to the previous comprehension questions (overall)?
  - difficulty: How do you rate the difficulty level of the passage you read?
  - familiarity: How familiar are you with the topic of this passage?
  - interest: How interesting this passage was?
  - pressured: How much pressure did you feel during reading?
  - sleepiness How sleepy were you during reading this passage
  - sleephours: How long did you sleep last night?(0: less than 3 hours, 1: 3-6 hours, 2: 6-9 hours, 3: more than 9 hours)
  - recognition: Have you read this passage before? (0:no, 1:yes)	



Citation:
```
@inproceedings{ahn2020towards,
  title={Towards predicting reading comprehension from gaze behavior},
  author={Ahn, Seoyoung and Kelton, Conor and Balasubramanian, Aruna and Zelinsky, Greg},
  booktitle={ACM Symposium on Eye Tracking Research and Applications},
  pages={1--5},
  year={2020}
}
```
