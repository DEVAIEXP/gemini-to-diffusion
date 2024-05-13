# Gemini-To-Diffusion


## About

This project was developed for the <b>Artificial Intelligence Immersion 2nd Edition</b> event promoted by Alura in partnership with Google. Gemini-to-Diffusion aims to make it easier to create prompts for imaging stable diffusion models. The user simply needs to ask Gemini in the chat what they want to generate in the image and Gemini will take care of generating a sophisticated prompt for stable diffusion inference. The image is generated in real time, making it possible to download it as a file. To generate the image, the application will send the prompt via REST API to a diffusion model hosted on the <a href=https://huggingface.co/>HuggingFace</a> platform.

## Application Colab Notebook
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](/notebook/colab-gemini-to-diffusion.ipynb)

## Local Instalation
Have the Python environment version 3.10.* and the Python virtual environment installed.

Then run the following command at the command prompt:
```bash
git clone https://github.com/DEVAIEXP/gemini-to-diffusion.git
cd gemini-diffusion
(no linux  ) source install_linux.sh
(no windows) install_windows.bat
```
Alternatively, if you want to install manually:
```bash
git clone https://github.com/DEVAIEXP/gemini-to-diffusion.git
cd gemini-diffusion
pip install -r requirements.txt
```

### Aditional parameters for installation scripts (Optional):
Assuming **T** for True and **F** for False:
* Entering T in the first parameter will force the deletion of the current Venv generating a clean installation.
```bash
(no linux  ) source install_linux.sh T
(no windows) install_windows.bat T
````
* Entering F in the second parameter will disable Venv during installation. Use this option if you do not want to use your own virtual environment.
```bash
(no linux  ) source install_linux.sh F F
(no windows) install_windows.bat F F
````
## Running local
**If you ran the installation without Venv, you will need to edit the script files and change the USE_VENV variable to the value 0 before starting to run the tool. To start, run the command:**

```bash
(for linux  ) source start.sh
(for windows) start.bat
```

# Interface Parameters
## Tab Chat
This tab is where the conversation with the model takes place, the following fields are available:

* `Question`: In this field, type the question for the Gemini model. To generate prompts for broadcasting, you must always use the /imagine command before the question. If the command is omitted the prompt will not be generated and the conversation will be treated as a chat conversation with the Gemini model.
* `Chat model`: List of available 'Gemini' model versions.
* `Image Model`: List of stable diffusion models available for use in the API.
* `Generated Image`: The image generated after generating the prompt.

### Tab Settings
In this tab, the parameters for activating the models and inference are informed:

* `Google API Key`: Google AI Studio API key for using Gemini models. Get your key here [Google API Key](https://aistudio.google.com/app/apikey/?utm_source=website&utm_medium=referral&utm_campaign=Alura&utm_content=).
* `Huggingface API Key`: Huggingface API key for using diffusion models. Get your key here [Huggingface API Key](https://huggingface.co/settings/tokens). Register and log in to get the key.
* `Temperature`: The parameter controls the degree of randomness in the token selection. Temperature is used for sampling during response generation, which occurs when top P and top K are applied. Lower temperatures are good for commands that require a more deterministic or less open-ended response, while higher temperatures can lead to more diverse or creative results. A temperature of 0 is deterministic, meaning the highest probability response is always selected.
* `Top P`: The top P parameter changes how the model selects tokens for output. The tokens are selected from most to least likely until the sum of the probabilities is equal to the value of top P. For example, if tokens A, B, and C have a probability of 0.3, 0.2, and 0.1 and the top P value is 0.5, the model will select A or B as the next token using the temperature and will exclude C as a candidate. The default value of top P is 0.95.
* `Top K`: The parameter changes how the model selects tokens for output. A top K value of 1 indicates that the selected token is the most likely among all in the model vocabulary (also called greedy decoding), while top K of 3 means that the next token is selected from the three most likely to use the temperature . For each step of token selection, the top K tokens with the highest probabilities are sampled. The tokens are further filtered based on top P with the final token selected by temperature sampling.
* `Max output prompt tokens`: Specifies the maximum number of tokens that can be generated for the prompt response.
* `Max output tokens`: Specifies the maximum number of tokens that can be generated in responses in general.

## Known issues
During execution, some problems may occur:
* Black screen on image: This is a broadcast decoder problem that may occur.
* Error message "Oops! there was an error generating your response...": Hugginface's broadcast API is not always ready to return a response when requested, there is a "cold start" of the model that can lead to a timeout , however. In this situation, just try again after a few seconds until the API can respond normally.

## Generated examples
### A cat
<p align="center">
  <img src="docs/0 - a cat.PNG">
</p>

### Winnie the Pooh
<p align="center">
  <img src="docs/1 - pooh.PNG">
</p>

### A pitbull
<p align="center">
  <img src="docs/2 - pitbull.PNG">
</p>

### A boy
<p align="center">
  <img src="docs/3 - a boy.PNG">
</p>

## License
This project is under [MIT license](LICENSE).

## Contact
If you have any questions or suggestions, feel free to send your question to the email: contact@devaiexp.com