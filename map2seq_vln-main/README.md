
## Workflow without Images 
(no need to download and preprocess panoramas)

### Preparation
```
pip install -r requirements.txt
```

### Inference and Evaluation
```
python vln/main.py --test True --dataset map2seq_unseen --config outputs/map2seq_unseen/noimage/config/noimage.yaml --exp_name noimage --resume SPD_best
```

### Train from Scratch:
```
python vln/main.py --dataset touchdown_unseen --config configs/noimage.yaml --exp_name no_image
```






#
## Workflow with Images

### Panorama Preprocessing
Unfortunately we are not allowed to share the panorama images or the ResNet features derived from them. You have to request to download the images here: https://sites.google.com/view/streetlearn/dataset  
Then change into the `panorama_preprocessing/last_layer` or `panorama_preprocessing/fourth_layer` folder and use the `extract_features.py` script. 

### Preparation
```
pip install -r requirements.txt
```

### Test
```
python vln/main.py --test True --dataset touchdown_seen --img_feat_dir 'path_to_features_dir' --config link_to_config --exp_name 4th-to-last --resume SPD_best
```

The `path_to_features_dir` should contain the `resnet_fourth_layer.pickle` and `resnet_last_layer.pickle` file created in the pano preprocessing step.


### Train from Scratch:
```
python vln/main.py --dataset touchdown_seen --img_feat_dir 'path_to_features_dir' --config configs/4th-to-last.yaml --exp_name 4th-to-last
```

References
=========

Code based on https://github.com/VegB/VLN-Transformer  
Touchdown splits based on: https://github.com/lil-lab/touchdown  
map2seq splits based on: https://map2seq.schumann.pub  
Panorama images can be downloaded here: https://sites.google.com/view/streetlearn/dataset

