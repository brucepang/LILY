# How to run a trained model on Codalab and submit it for evaluation?

We use [Codalab](https://worksheets.codalab.org/) to evaluate models and display their scores on the [leaderboard](https://stanfordnlp.github.io/coqa/).
We show you how to run pretrained baseline model but you could use a similar set up for your model.

Before you run on Codalab, first you have to make sure you have a docker environment that can run your code.
In the baseline model case, we require torch=............
You can create your own docker that satisifies your requirements, or you can use existing ones on https://hub.docker.com/.
We recommend https://hub.docker.com/r/floydhub which contains dockers for almost every deep-learning framework.
We will use https://hub.docker.com/r/floydhub/pytorch/tags/, particularly, _____________.
However this docker does not contain ___________, so we install them later using pip.
Follow these steps one by one to run our model on Codalab.

## 1. Install codalab client to upload data from command line
See https://github.com/codalab/codalab-worksheets/wiki/CLI-Basics#installation

## 2. Create a worksheet
Go to https://worksheets.codalab.org and create a worksheet.
Say you call this username-spider-baseline

## 3. Upload data to that worksheet
Run the following command from your terminal to switch to that worksheet first.

```
  cl work main::username-spider-baseline
```

Download data to your local system and upload it to that worksheet. You can also use the web-interface to upload data if the data is in tar/zip format and then untar/unzip. If you use web-interface, you can skip steps 1 and 2.

```
  git clone _____
  cl upload spider-baselines
```

Add dev-file to your worksheet.

```
  cl add bundle _____ .
```

## 4. Install requirements and run the code
[run_on_codalab.sh](run_on_codalab.sh) installs the requirements and runs the code. On the codalab worksheet's web terminal, run the following command which specifies the docker, number of gpus, cpu memory, etc.

```
  cl run :spider-dev-v1.0.json :spider-baselines 'sh spider-baselines/run_on_codalab.sh' --request-docker-image ______________ --request-network --request-gpus 1 --request-memory 6g
```

The resulting worksheet looks like this _______

You can access the final predictions in [baseline_combined_model/predictions.combined.json](https://worksheets.codalab.org/______________________)

Email ______@yale.edu when you can run your model successfully.
