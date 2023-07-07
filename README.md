# Adversarial Decoder
This is the official repository for PETS 2023 paper "Towards Sentence Level Inference Attack Against Pre-trained Language Models"
The goal is to let you train a decoder, which can invert embeddings and test its performances.


# Dependencies
To use the code in this project, make sure your Python=3.6 

All the codes are provided in notebook for interpretability

Please refer to environment.yml

# Datasets
Use the links below to access the datasets used in our paper. However, we found that CMS website has been updated and the original link doesn't work anymore.

Skytrax: https://github.com/quankiquanki/skytrax-reviews-dataset

Twitter US Airline: https://github.com/benhamner/crowdflower-airline-twitter-sentiment

CMS: https://data.cms.gov/search

MT: https://www.kaggle.com/datasets/tboyle10/medicaltranscription

# Preprocess for keyword inference attack

We provide a sample preprocessing notebook for annotating medical datasets.

As for airline datasets, we refer to the word city dataset as a benchmark: https://github.com/datasets/world-cities


# Tips for Data Preprocessing
For example, to preprocess Skytrax dataset.
We prepare two versions of dataset: the full dataset and a filtered dataset.
We refer to the external word city dataset, and only keep the samples containing one of the cities.
If the decoder is trained on the filtered dataset, we refer it as vanilla decoder as in the paper.
If the decoder is pre-trained on the full dataset then finetuned on the filtered dataset, we refer it as pre-trained decoder.


# Preprocess for training the decoder
The preprocessing pipeline is given for BERT. However, it can be adapted to other LMs.

Run preprocess_tokens.ipynb to generate input_ids etc. for LMs (Hint: Clean your own textual data before performing any preprocesses)

Run generate_embedding.ipynb to generate sentence embeddings for decoder

# Train the Decoder
Follow the toy-decoder.ipynb to train and test the decoder
1. The Decoder class is the model used in our experiment, and smooth entropy loss is used for training.
2. The training epoch is set to be 20 with early stop.
3. After training is done, use translate function to query the decoder and generate sentences. By default, top-k sampling is used and each sample is repeated 10 times.
4. Finally, we can either count the keywords in the generation or measure the sentence similarity directly.

# Sample dataset
we provide a subset of mt with spacy annotations. You can prepare your own dataset in this fashion.

# Sample code
We provide a step by step notebook to help you perform data preprocessing and decoder training using the sample dataset.
You are encouraged to run it on google colab and follow the instructions to train the decoder. After that, we should be able to experiment embedding
inversion on your own data. 
