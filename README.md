# Bicycle Bell Sound Event Detection Pipeline
**Author: Clemens Kubach**

This repository is one of three for my bachelor thesis on "Development of an Embedded System 
for Detecting Acoustic Alert Signals of Cyclists Using Neural Networks".

It contains the ML-pipeline for inspecting and preparing the datasets, training the neural networks and evaluating them on hold-out data for atomatically detecting the sound event of cyclists using their bicycle bell. Written in Python 3.9.

The other related repositories are:
- [bicycle-bell-sed-models](https://github.com/ClemensKubach/bicycle-bell-sed-models)
- [bicycle-bell-sed-software](https://github.com/ClemensKubach/bicycle-bell-sed-software)


## Dependencies
There are two types of dependencies used for this project:
- Python package dependencies
- Data dependencies

### Python Package Dependencies
The pip dependencies can be installed via the `requirements.txt`. 
To train a model, you also have to install the package from the repository [bicycle-bell-sed-models](https://github.com/ClemensKubach/bicycle-bell-sed-models.git). 
You can install it via:
```shell
pip install git+https://github.com/ClemensKubach/bicycle-bell-sed-models.git
```

If it is private, you need granted permissions to this repo and use a personal access token. 
Then, the following command can be executed:
```shell
pip install git+https://{gh_token}@github.com/ClemensKubach/bicycle-bell-sed-models.git
```
This is also already in use within the notebook.


### Data Dependencies
The notebook supports two types of data sources to run its cells:
- the Google Cloud Storage (GCS) bucket and
- the exported bucket as Zip file

During the development GCS was used and therefore the code is mainly based on it. 
However, it should also be feasible without problems or with only a few adjustments locally with the data from the zip backup.

To access the GCS bucket, you have to use the .json key when asked via the notebook. A key file can be asked from the author. Thus, you have access to request data from this bucket. Alternatively, you can upload the folders in `thesis-bicycle-bell-sed-bucket` of the zip file to your own bucket.

For using the local bucket from the zip file directly without GCS:
- unpack the zip file
- use the folder `thesis-bicycle-bell-sed-bucket` as root folder and set `USE_GCS=False` within the notebook.

Using GCS for inspecting/reading the results, is recommended. For further development, you can use your own GCS bucket or using the local bucket via the zip.


## Usage
**It was extensively tested with Google Colab with use of Google Cloud Storage bucket. The models were trained on a Colab GPU instance.**

The jupyter notebook can be inspected without running on any system. 
For executing the cells, follow the instructions given in the notebook.

In the most cases, it is not necessary and **not recommended** to simply run **all cells**, because they are generating a lot of data and traffic.
This is already done and the prepared files can be found in the Google Cloud Storage bucket or the backup zip file of the bucket.
I.e., the trained models can also be found in GCS and can be loaded directly within the evaluation chapter.
