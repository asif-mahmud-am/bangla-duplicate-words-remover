# bangla-duplicate-words-remover

This is a Bangla Duplicate Words Remover tool that can remove duplicate words from a given sentence. But it is also intelligent enough to identify Bangla "dirukto" words and it does not remove them. 

# Dataset 

The dataset is prepared from the popular bangla newspaper [Prothom Alo](https://www.kaggle.com/datasets/twintyone/prothomalo?select=content_2016.csv), and [Bangla Oscar dataset](https://huggingface.co/datasets/oscar/viewer/unshuffled_deduplicated_bn/train). 

As this is a sequence classification problem, there are two labels - right duplicates (0) and wrong duplicates (1) 

We have labeled collected sentences containing correct duplicate words 0. 
As for sentences with wrong duplicate words, we have generated error sentences by corrupting a correct sentence by duplicating a word at a random position. We labeled them as 1. 

We have finally prepared a dataset with data:

Train: 

    14M rows  [Equal number of 0's and 1's]
    
Test :

    70k rows [Equal number of 0's and 1's]

A demo of the dataset is in the repository. 

# Model 

We have fine-tuned the [bangla-bert-base](https://huggingface.co/sagorsarker/bangla-bert-base) model by Sagor Sarker for sequence classification task. 

# Train 

Training info:

Tokenizer max len: 256
lr=5e-5
Batch size =32
Epochs = 3
Optimizer: AdamW 
Training time needed: 14 hrs on a single 3090 GPU. 

# Result 

A 95.18% accuracy on the test dataset (70k). 

classification report: 

<img src=https://github.com/asif-mahmud-am/bangla-duplicate-words-remover/assets/65419625/4ce77ab6-26f3-40b4-8008-2652bae2b96c>

The training and testing notebook is provided in the codebase! 

