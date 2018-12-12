# Tourism_chatbot_RasaNLU
This project aims at testing RasaNLU by improving intents classification and entities extraction of a tourism chatbot.<br>
To achieve that we try two pipelines (spacy_sklearn, tensorflow_embedding) and different components of both pipelines.<br>
Therefore, this is a first part towards building a tourism chatbot with Rasa; the second being the training of a Rasa Core model.<br>
The notebook contains a test an evaluation of both tensorflow and spacy pipelines with increasing training data sizes. It appears that tensorflow_embedding is much faster and gives a very good accuracy while spacy has scalability problems and gives bad results. For more details, take a look at the notebook.

# Installation

## Prerequisites
In order to run the project, you need to have the following packages installed:<br>
* Python
* [Rasa NLU](https://rasa.com/docs/nlu/installation/): `pip install rasa_nlu`

## Installing

Clone the repository using Git:

```
$ git clone https://github.com/lionelsome/Tourism_chatbot_RasaNLU.git
$ cd Tourism_chatbot_RasaNLU
```

## Running the tests
* Install Rasa NLU pipelines:
> For **spacy_sklear**: 
```
pip install rasa_nlu[spacy]
python -m spacy download en_core_web_md
python -m spacy link en_core_web_md en
```
> For **tensorflow_embedding**:
```
pip install rasa_nlu[tensorflow]
```

* Train the Rasa NLU model
`python -m rasa_nlu.train -c config.yml --data data/training_data.json -o models --project current --verbose`
where `config.yml` should be either spacy_config.yml or `tensorflow_config.yml` depending on the pipeline you want to use.<br>
The folder `data` contains the training and test data set to use.<br>
The model is stored under the directory `models/current/model_xxx_xxx` where xxx are the date and time.

* To evaluate the model, you can use [Rasa NLU `evaluate`](https://rasa.com/docs/nlu/evaluation/) mode like this:<br>
```
python -m rasa_nlu.evaluate --data data/test_data.json \
       --confmat CONFMAT --histogram HISTOGRAM \   
       --model models/current/model_xxx-xxx
```
