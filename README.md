## Python version
[Haystack](https://github.com/deepset-ai/haystack) is not very happy with the latest python (3.10). So the first steps is to install a slightly older python version (3.8.6). We are using [pyenv](https://medium.datadriveninvestor.com/how-to-install-and-manage-multiple-python-versions-on-linux-916990dabe4b) to run multiple python versions concurrently.


## Elastic Search
Haystack needs a document store and Elastic search is the most compatible one. Instructions on how to run one in docker is [here](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)

## Create and activate the virtual environment

```
python -m venv .env

source .env/bin/activate
```

## Install required packaages
Its difficult to find a torch version that works with haystack and also has the latest CUDA. The best one I found is this one:

```
pip install torch==1.10.2+cu111 -f https://download.pytorch.org/whl/torch_stable.html
```

Run the following to check torch and cuda versions

```
python cuda.py
```

## Install Haystack
The recommendation is to install Haystack from soure.

```
git clone https://github.com/deepset-ai/haystack.git
cd haystack
pip install -e '.[all-gpu]'
```

If you cannot upgrade pip to version 21.3 or higher, you will need to replace:

```
'.[all-gpu]' with '.[sql,only-faiss-gpu,only-milvus1,weaviate,graphdb,crawler,preprocessing,ocr,onnx-gpu,ray,dev]'
```

## Jupyter

This should start jupyter lab inside the same virtual environment
```
pip install jupyterlab
pip install ipywidgets
jupyter lab
```

## Hugging Face dependencies

```
pip install datasets
```