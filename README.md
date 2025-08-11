# Json-Notebook-Converter (notebookify.py)
A small script to convert between valid jupyter python notebooks (.ipynb) and their Azure Synapse equivalent json file. 

## Installation
Save the script to your machine. Then you can either add its folder to your path variable or create an alias to it for easy access.

I use git bash, so I have this in my `aliases.sh` for the shortest usage:

    alias notebookify='python C:/Dir/To/Script/notebookify.py'

Then it's just `notebookify args` in git bash.

## Usage

#### To convert synapse json files to valid notebooks:

    python notebookify.py file1.json file2.json file3.json ...

or to convert all (could be a little excessive):

    python notebookify.py *.json


#### To convert all _LOCAL.ipynb notebooks in the working dir back to synapse json:

    python notebookify.py -j
 
## Git Ignore
When converting to ipynb, the script saves the notebook as `[filename]_LOCAL.ipynb`, which you can then edit as needed. The synapse-specific metadata (spark configuration and the like) will be stored as `[filename]_METADATA.json`. 
If you wish you can include the following lines in your `.gitignore` to easily keep these out of the repo:

    *_LOCAL.ipynb
    *_METADATA.json

## File Creation
This util is handy for existing files, but if you want to create a new notebook you should still create and commit it through the Synapse Analytics web editor. Synapse tracks a bunch of fields in the metadata that VSCode won't know to populate (and will actively meddle with if allowed).
