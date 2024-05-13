# This is our pytorch implementation for RFADT

## Environment Requirement
The code has been tested running under Python 3.9.18. To install the required packages, run the following command in the project terminal:
```
pip install -r requirements.txt
```

## Datasets
The directory structure and description of the dataset are as follows:
  *  .\dataset\douban\train.csv, .\dataset\douban\valid.csv, .\dataset\douban\test.csv, .\dataset\douban\social.csv.
  *  Each line in the train.csv, valid.csv and test.csv is a user with her/his positive interactions with items: userid \ itemid.
  *  Each line in the social.csv is a user with her/his positive interactions with friends: userid \ friendid.

The original datasets for Yelp, Ciao, LastFM, Douban can be found in directory: .\dataset\raw_data.

## Baselines
All baselines are open source.
  * NGCF: https://github.com/xiangwang1223/neural_graph_collaborative_filtering
  * LightGCN: https://github.com/kuandeng/LightGCN
  * Diffnet: https://github.com/PeiJieSun/diffnet
  * SocialLGN: https://github.com/leo0481/SocialLGN
  * SoNeuMF: https://github.com/wave-zuo/SocialNCF
  * ECGN: https://github.com/wubinzzu/ECGN
  * MGL: https://github.com/weicy15/MGL


## Examples to run RFDAT
This is an example of running RFDAT on the Douban dataset.
  * To train, run [main.py](./main.py) with command line:
```
python main.py --model RFDAT --dataset douban --preitemrelation --trainbatch 2048 --g_batch 4096 --ilayers 3 --hdim 64
```
  * To test, run [myeval.py](./myeval.py) with command line:
```
python myeval.py --model RFDAT --dataset douban --hdim 64 --ilayers 3 --pretrainmodel ./save/xxxxx
```

NOTE :
  * all recommendation models predict each user's link scores to all of its non-interactive items.
  * the duration of training and testing depends on the running environment.
  * set model hyperparameters on .\code\myparse.py.
  * the log file save at .\code\log.
