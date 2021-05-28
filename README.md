gptcmd 1.0.1
==============

gptcmd is a command line utility that allows the user to describe command line tasks using natural language and recieve commands generated by OpenAI's GPT-3 API. Context is provided by ```train.txt``` to fine tune GPT-3 for this text generation task. OpenAI and API Documentation: https://beta.openai.com/docs/api-reference/introduction

Installation
--------------

### Obtaining gptcmd

It is recommended to clone the GitHub repository of gptcmd such that you can pull in new updates at any time (if available). Open a new terminal and clone the repository using

    git clone https://github.com/atc0m/gptcmd.git

This will clone gptcmd in your current folder in a new folder named gptcmd. Now enter the folder using

    cd gptcmd

### Using gptcmd without installation

You can run gptcmd as any user without installation. Export the environment variable GPT_TOKEN="PERSONAL TOKEN" with your personal OpenAI API Token. The gptcmd usage is simple just provide instructions for a command:

    ./gptcmd list all files in this directory

### System installation (optional)

A makefile file provided for easy installation. The default location for gptcmd is in ```/usr/bin```. If you want to install to your system you can run:

    sudo make install

You can verify that gptcmd was installed correctly by entering:

    which gptcmd

OpenAI API token has to be set as GPT_TOKEN environment variable or saved in the ```~/.gptcmd/credentials``` file. Model configuration can be found in ```/etc/gptcmd/gptcmd.conf```

    - ```ENGINE``` The ID of the engine to use for this request.
    - ```TEMPERATURE``` Higher values means the model will take more risks.
    - ```TOP_P``` 0.1 means only the tokens comprising the top 10% probability mass are considered. probability mass.
    - ```MAX_TOKENS``` The maximum number of tokens to generate. Maximum 2048 with prompt and completion
    - ```PRESENCE_PENALTY``` Increases the model's likelihood to talk about new topics.
    - ```FREQUENCY_PENALTY``` Decreases the model's likelihood to repeat the same line verbatim.

### Examples

    Q: gptcmd gptcmd find all file bigger than 1gb
    A: find / -size +1G

    Q: gptcmd find the most frequently used word on website https://beta.openai.com/
    A: curl https://beta.openai.com/ | grep -oP '\w{1,}' | sort | uniq -c | sort -n
