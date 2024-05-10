# This is our pytorch implementation for RFADT

## Environment Requirement
The code has been tested running under Python 3.9.18. To install the required packages, run the following command in the project terminal:
```
pip install -r requirements.txt
```

## Dataset
We provide douban dataset used in the experiment.
  *  .\dataset\douban\train.csv, valid.csv, test.csv, social.csv.
  *  Each line in the train.csv is a user with her/his positive interactions with items: userid \ itemid.
  *  Each line in the social.csv is a user with her/his positive interactions with friends: userid \ friendid.

The original datasets for Yelp, Ciao, LastFM, Douban can be found in directory: .\dataset\raw_data.

## Examples to run RFDAT:

To train, run [main.py](./main.py) with command line:
```
python main.py --model RFDAT --dataset douban --preitemrelation --trainbatch 2048 --g_batch 4096 --ilayers 3 --hdim 64
```
To test, run [myeval.py](./myeval.py) with command line:
```
python myeval.py --model RFDAT --dataset douban --hdim 64 --ilayers 3 --pretrainmodel ./save/xxxxx
```

NOTE :   
(1) the duration of training and testing depends on the running environment.  
(2) set model hyperparameters on .\code\myparse.py  
(3) the log file save at .\code\log
