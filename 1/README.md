# Hệ thống gợi ý phim
Xây dựng hệ gợi ý phim bằng Neighborhood-based Collaborative Filtering và Content-based Recommendation System.

## Install requirements
```
$ pip install -r requirements.txt
```

## Datasets
Using a subset of MovieLens 20M dataset: [Original-dataset](https://files.grouplens.org/datasets/movielens/ml-20m.zip).

Download the subset of the original dataset at [movielens20m-subset](https://drive.google.com/file/d/1u4TY7lml7liOHzyBQGruVTm4QS2zTiqW/view?usp=sharing) to "/data"


----------------------------------------------
## Collaborative filtering
### Train model
To train the collaborative filtering model, run the following command
```
$ python collaborative_filtering.py
        -k              # int: Number of neighbors. Default: 30
        --uu            # bool: User-user collaborative filtering. Default: True
        --save_name     # str: Name of the saved model. Default: None
        --save_dir      # str: Where to save the model. Default: /models 
	--data_dir	# str: Data directory. Default: /data
```
If save_name is None, then model name is cf_{k}.pkl


----------------------------------------------
## Content-based recommendations

### Preprocessing
Install gensim and preprocess
```
$ pip install gensim
$ python preprocessing.py
```
or download preprocessed data to '/data': [preprocessed-data](https://drive.google.com/file/d/1wJl1-1t3U93T12u9jlxmzMQcneEx7OWE/view?usp=sharing)

### Train model
```
$ python content_based.py
        --save_name     # str: Name of the saved model. Default: None
        --save_dir      # str: Where to save the model. Default: /models 
	--data_dir	# str: Data directory. Default: /data
```
If save_name is None, then model name is cb.pkl


----------------------------------------------
## Get recommendation
```
$ python recommend.py 
        -- topk         # int: Number of recommendation. Default: 5
        -- user_id      # int: User to get recommendation. 
                        # Must be between 0 and 999. Default: -1
        -- model_name   # str: Model used to recommend. Default: cf_40.pkl
        
