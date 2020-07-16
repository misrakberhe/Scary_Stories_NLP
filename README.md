# Scary Stories!

The goal of this project is to generate scary stories using Transformer models. I want stories that can either stand on their own or be something a writer can bounce off of.

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

### How to Train

### Code Acknowledgments

The code to generate the contextual parts of each example, like the text or title.
https://gist.github.com/ageitgey/d7eae5eab1be8eaad48ac387faf49831
