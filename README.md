# PointNetVlad-Pytorch
Unofficial PyTorch implementation of PointNetVlad (https://github.com/mikacuy/pointnetvlad)

:warning: This repository is not maintained. Any questions regarding the approach should be directed to the authors of the original implementation: https://github.com/mikacuy/pointnetvlad

I kept almost everything not related to tensorflow as the original implementation.
The main differences are:
* Multi-GPU support
* Configuration file (config.py)
* Evaluation on the eval dataset after every epochs

This implementation achieved an average top 1% recall on oxford baseline of 84.81%

### Pre-Requisites

```
apt-get update
pip install pandas
```

* PyTorch 0.4.0 (but infact no Dataloader is inherited, instead of manully implemented)
* tensorboardX

### Generate pickle files
```
cd generating_queries/

# For training tuples in our baseline network
python generate_training_tuples_baseline.py

# For training tuples in our refined network
python generate_training_tuples_refine.py

# For network evaluation
python generate_test_sets.py
```

### Before train
+ remove the dummy code `os.environ["CUDA_VISIBLE_DEVICES"] = "3"`, which may crash the procedure.

### Train
```
python train_pointnetvlad.py --dataset_folder $DATASET_FOLDER
```

### Evaluate
```
python evaluate.py --dataset_folder $DATASET_FOLDER
```

Take a look at train_pointnetvlad.py and evaluate.py for more parameters
