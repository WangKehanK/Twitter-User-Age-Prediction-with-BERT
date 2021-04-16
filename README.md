# Twitter-User-Age-Prediction-with-BERT

## How?

First, input the user's tweets into the BERT separately. Second, concatenate the BERT's last 4 layers of [CLS] to represent a tweet as a vector. Third, Average all vectors of the tweets for each user, so each user has a vector representation. Then, the vector is mapped to a smaller vector through a layer of fully connected neural networks. Finally, the vector is mapped to a range of 0-1 by the fully connected neural network following the Sigmoid activation function for classification. When the value is greater than or equal to 0,5, the user's age is predicted to be greater than or equal to 21, otherwise less than 21. As a result, I improve the accuracy from 63%(Lexicon) to 76.9%
