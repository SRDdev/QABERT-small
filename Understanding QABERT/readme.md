# BERT

# Bidirectional Encoder Representation from Transformer

*Pre-requisite : Need to have basic understanding of transformers*.

Bidirectional Encoder Representation Transformers (BERT) were introduced in 2018 by Google. This architecture is far superior to LSTMs as it captures the context of words in a sentence better than LSTMs.

## Problems to Solve
- Neural Machine Translation
- Question Answering
- Sentiment Analysis
- Text Summarization

## Training
Training of BERT models takes place in two parts:
- Pre-Training: The entire Transformer is trained to understand language.
- Fine-Tune: Only the Encoder part of the Transformer is trained on a specific task (e.g. summarization).

## Pre-Training
The main goal of pre-training is to allow the model to understand language and context. This is achieved by training BERT on two unsupervised tasks: masked language modeling and next sentence prediction.
1. Masked Language Modeling: In this task, the model receives a sentence with some words masked, and it has to predict the masked words. This allows the model to understand the language of the sentence.
2. Next Sentence Prediction: In this task, the model receives two sentences and has to predict if the second sentence follows the first sentence. This allows the model to understand the context of different sentences.

## Fine-Tuning
Fine-tuning is the process of further training a deep learning model on a specific task after pre-training. It usually involves re-training the last few layers of a pre-trained model using task-specific data. This allows the model to adapt to the new task and produce better results. By fine-tuning a pre-trained model, time and resources can be saved, as the model is already trained on the general features of the dataset. The fine-tuned model can then be used for the specific task it was trained on.

BERT can be further trained on specific NLP tasks like summarization and question-answering by replacing the last few layers of the architecture with preferred ones and training the model on the required dataset. As the model only needs to learn the last few layer parameters from scratch, the training time is very low.

## Embeddings
Embeddings are compact and condensed representations of original text, where each word or piece of text is mapped to a unique vector in a high-dimensional space. 
The initial embeddings for BERT consist of three embeddings:
- Token Embeddings: Encoding words into vectors (Word Piece)
- Segment Embeddings: Encoding sentence numbers into vectors
- Positional Embeddings: Encoding the position of the embedding in the sentence.

The positional and segment embeddings are required for temporal understanding as all these vectors are fed into the model simultaneously.

## Output
All word vectors generated in the output are generated simultaneously. However, these numbers are not meaningful to humans, so a linear layer with SoftMax activation is added at the output of the model. The size of this layer should be equal to the vocabulary size used to encode the inputs (e.g. Word Piece: 30k). This converts the outputs into a distribution. The new distribution and the actual distribution are used to compute the loss of the model.
