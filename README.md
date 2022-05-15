# Research Paper Classification by Abstract

## Authors
Elijah Tamarchenko, Williams College
Huandong Chang, Grinnell College

## Abstract
In this project, we build a Natural Language Processing (NLP) pipeline and apply LSTM and DistilBERT models to predict which subject a research paper belongs to based on its abstract. Our dataset consists of 15,000 papers from the arxiv dataset on Kaggle, 60\% (9,000) of which are used for model training. Paper subjects are uniformly distributed among Computer Science, Mathematics, Physics, Quant. Bio, and Statistics. With the limited amount of computing power and training data, the LSTM model reaches 86\% accuracy and the DistilBERT model reaches 92\% accuracy in the testing test. 

## Dataset
Our dataset is from the arxiv dataset on Kaggle, with over 1.7 million scholarly papers across STEM. Since our computing power is limited, we only extract 15,000 papers from the arxiv dataset and use 60\% (9,000) for model training, 20\% for the validation set, and 20\% for the testing set. 

Dataset Link: https://www.kaggle.com/Cornell-University/arxiv?select=arxiv-metadata-oai-snapshot.json


## Models

### Model 1: Long short-term memory (LSTM)
LSTM is a type of recurrent neural network that can keep track of long-term dependencies in the input sequences. After data preparation and tokenization, we use a sequential model with four layers: a) Embedding; 2) Spatial Dropout 1D; 3) LSTM with 128 units (output dimensionality); 4) Dense layer with softmax activation for subject prediction. 


### Model 2: DistilBERT
DistilBERT (Sanh et. al, 2020) is a transformer model based on the BERT architecture. Since the size of the model was a big consideration for us, DistilBERT was the better choice as it is 40\% the size of the BERT model and 60\% faster, while compromising only 3\% on accuracy. This is done using knowledge distillation, compression, and improvements in the linear algebra operations used for computation. Besides this, the model's architecture is the same, with an adjustment to the number of layers and neurons in the model. 


## Results

Overall, the LSTM Model has given us 86\% accuracy and the DistilBERT model gives 92\% accuracy in the testing subset. For both models, Physics paper is the most distinguishable of all the fields (more sensitive and more precise), Math and Quant. Bio have decent performance, while Computer Science and Statistics are harder to identify and are sometimes confused with each other. After analyzing the misclassifications, we find out that a lot of the papers that are misclassified by the model seem to fall under the intersection of computer science and statistics, even though they are only classified as statistics.

## Discussion
From the result, we know the DistilBERT model's accuracy is 6\% higher than the LSTM model. This makes sense, as the DistilBERT model is a finetuning of a large state-of-the-art model which is used for lots of other NLP tasks, and thus would perform a lot better. Also, the use of transformers allows the model to use the context of the abstract for each word in it, rather than sequentially building up from left to right as the LSTM, and this bidirectionality could allow for more accuracy. We believe accuracies of 86\% and 92\% are very impressive for a model that is only reading the abstract. We postulate that further research would show that reading more parts (such as the conclusion part) of each scientific paper would probably provide higher accuracy for either model, as it would provide a lot more context to the transformer model as well as the LSTM model.

