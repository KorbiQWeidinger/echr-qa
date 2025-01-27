# AQuAECHR Benchmark

This repository contains the code needed to evaluate model performance on AQuAECHR.
It also contains the code needed to reproduce our conducted experiments.

The AQuAECHR dataset can be found under `data/echr_qa_dataset.csv`.
The results of all our experiments can be found in the `data` folder.

## Setup Instructions

#### Create an environment and install dependencies

```
python -m venv env
source env/bin/activate
pip install -r requirements.txt
```

Download `en_core_web_trf` to split text into sentences

```
python -m spacy download en_core_web_trf
```

#### Environment variables

To conduct some of our experiments we used APIs instead of running them on our own GPUs.
If the APIs are still available, tokens are required to access them.

```
HUGGINGFACE_TOKEN=***
GROQ_API_KEY=***
DEEPINFRA_API_KEY=***
```

## Running experiments

The names of all experiments can be found in `src/experiments/load_experiment.py`

```
python experiment.py --experiment rag_gtr_k_10_llama_8b --device cuda:0
```

## Running evaluations

```
python eval.py --experiment rag_gtr_k_10_llama_8b --device cuda:0
```

Note that `eval.py` does not include mauve_scores;
they can be obtained by running `python mauve_score.py --experiment rag_gtr_k_10_llama_8b`.

To obtain final results use `eval.ipynb`.

## English ECHR Cases DB

To get most cases one can use the DB provided by [https://echr-opendata.eu/](https://echr-opendata.eu/). Note that we scraped a view additional cases.
To get our full GTR embeddings db or the english cases DB for BM25 that was used during our experiments contact us.
