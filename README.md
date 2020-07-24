# Scary Stories!

The goal of this project is to generate scary stories using Transformer models. I want stories that can either stand on their own or be something a writer can bounce off of. I created this project as my capstone for my Data Science Diploma. 

Here is a 3 minute presentation giving a general overview of what its about: https://www.loom.com/share/4baba399f75f48f780783aff4e1ed5df

### How to Generate Text

    Generate.ipynb

I would suggest if you plan on running this, to use a Google Colab session, the process of setting up the environment is going to be straight forward. The code below (also at the start of the notebook) will set up the environment and clone the Grover transformer model repo:

    %cd /content
    !git clone https://github.com/rowanz/grover.git

    %cd /content/grover
    !python3 -m pip install regex jsonlines twitter-text-python feedparser

    !pip install -r requirements-gpu.txt

    !pip install ujson

Next what you'll want to do, if you want some kind of specific output, is to adjust the article variable. You can adjust any value to what you want and it should attempt to generate a related text.

However, you should keep the domain as 'nosleep' if you want to see what the model does with the new data it was trained on. If you don't care too much about that, you can subsitute that value for any major news website url and it will try to produce a straight up news article. 

### How it was Trained

The model is adapted from the smallest version of the Grover one. Any modifications that I did were re-using what was already there. My general philosophy while training this model was to freeze the Grover model and add either layers or new transformers. The difference between my model and the Grover one is that I added an entire Transformer block every 4th Transformer block. 

One of the main methods I experimented with was taking the feed forward neural network and adding it into various locations and with various amount of layers, mostly at the end of the Transformer code, which often ended up with gibberish. The current state of the model has been my best iteration.

### Setting up data file

** to be added **

### How to Train

Starting with the Train.py file, once you load the grover repo, you will need to set up the Google Colab TPU for training. I attempted to use finetune the Mega version of Grover, but the TPU services couldn't handle a model that size and I'm not planning on paying for AWS TPUS at this point. The code to setup the TPU is pulled directly from Google Cloud instructions, a few modifications and you have your TPU ready.

Next what you want to do is adjust your learning rate, warmup steps and other parameters with the flags. You will need to copy the TF_MASTER into the TPU name (if your Google Colab session has been disconnected for a while, you will have to re-run that and make sure the TPU address is still the same).

In that same step, you will want to make sure you're pointing at the right places. Input file is your '.tfrecord' file with the data and your output directory has to be pointing to a Google Cloud bucket, like mine is.

At this point, you can train it. If you want to generate, you can just adjust the filepaths in the Generate.ipynb file. 

### Code Acknowledgments

The code to generate the contextual parts of each example, like the text or title.
https://gist.github.com/ageitgey/d7eae5eab1be8eaad48ac387faf49831
