
# Running the code (Instructions)
##Notes before running: 
1. Change `env.py` API key to your own actual API key. One in env.py is a dummy placeholder
2. Root folder must be `multimodal_enterprise_rag`. In the code, the folder used is `/content/drive/MyDrive/AI_Projects/multimodal_enterprise_rag` because I ran it on Google Colab and stored the files in Drive

## Option 1: Run the Colab Notebook
1. Navigate to the `rag_system` folder
2. Open `Copy of Enterprise_RAG.ipynb`
3. Run all the code blocks in order
4. User input is taken in the form of a function as `user_input(media_path,query)`

## Option 2: Use the files
1. Run the following commands: '''import os

os.chdir("/root")

!pip install -e .
'''
2. Run the next set of commands: '''import os

import sys

os.chdir("/root")

sys.path.append("/root")
'''
3. Navigate to `/root`
4. Run the following code: '''import importlib 

import rag_system.main as main 

importlib.reload(main) 

main.user_input(media_path,query)
'''



