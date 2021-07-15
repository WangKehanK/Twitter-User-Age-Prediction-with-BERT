# Twitter-User-Age-Prediction-with-BERT

## Introduction:

- Code: [Age](Twitter_User_Age.ipynb)
- Result: [prediction on Twitter labeled data](https://github.com/WangKehanK/Twitter-User-Age-Prediction-with-BERT/blob/main/data/age_prediction/Twitter_users_labeled_prediction.csv)
- Result: [prediction on Twitter unlabeled data(all user)](https://github.com/WangKehanK/Twitter-User-Age-Prediction-with-BERT/blob/main/data/age_prediction/Twitter_user_handles_to_prediction.csv)
- If you want to reproduce the prediction for unlabeled data, you can find the Fine tuned model, and tweets data [here](https://drive.google.com/drive/folders/1dyQDSu0x5muhUSvphLyvLdck2ArkfXU0?usp=sharing)


## The algorithm flow is as follows: 

First, input the user's tweets into the BERT separately. Second, concatenate the BERT's last 4 layers of [CLS] to represent a tweet as a vector. Third, Average all vectors of the tweets for each user, so each user has a vector representation. Then, the vector is mapped to a smaller vector through a layer of fully connected neural networks. Finally, the vector is mapped to a range of 0-1 by the fully connected neural network following the Sigmoid activation function for classification. When the value is greater than or equal to 0,5, the user's age is predicted to be greater than or equal to 21, otherwise less than 21. As a result, I improve the accuracy from 63%(Lexicon) to 76.9%

## Experimental setup: 

The data that is input into the Bert model for each user is stored within a list, and each element of the list is a string corresponding to its own tweet. Afterwards, all the steps as indicated in the previous section regarding our approach were followed. The learning rate was set to 5e-6, where a very high learning rate is not conducive to model training. We set the number of epochs for training at 10. The max sequence length was set to 18, and tweets that were too long or too short were truncated or padded to the specified length. Additionally, gradient accumulation was used to simulate the specified batch size. To ensure reproducibility, the random seeds were specified in advance. Finally, it's necessary to ignore users who don't have any tweets, and to avoid repeated crawling of data, the points were written to files for reuse.

