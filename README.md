# xERTE: Explainable Subgraph Reasoning for Forecasting on Temporal Knowledge Graphs
This repository contains code for the reprsentation proposed in the ICLR2020 xpaper titled "[Explainable Subgraph Reasoning for Forecasting on Temporal Knowledge Graphs](https://openreview.net/forum?id=pGIHq1m7PU)".

## Installation

- clone repository
- install virtualenv
```
pip install virtualenv
```
- create virtual environment
```
virtualenv -p python3 venv
```
- activate virtualenv
```
source venv/bin/activate
```
- install packages
```
pip install -r requirements.txt
```
- specify directory to save Checkpoint
```
cd tKGR
vim local_config.py
```
For example if you want to save checkpoints where local_config.py is

#### **`local_config.py`**
```python
from pathlib import Path
save_dir = Path(__file__).parent.absolute()
```
#### Run:
Training:
```
python train.py --warm_start_time 48 --emb_dim 256 128 64 32 --batch_size 128 --lr 0.0002 --dataset ICEWS14_forecasting --epoch 10 --sampling 3 --device 0 --DP_steps 3 --DP_num_edges 15 --max_attended_edges 40 --node_score_aggregation sum --ent_score_aggregation sum
python train.py --warm_start_time 48 --emb_dim 256 128 64 32 --batch_size 128 --lr 0.0002 --dataset ICEWS0515_forecasting --epoch 10 --sampling 3 --device 0 --DP_steps 3 --DP_num_edges 15 --max_attended_edges 40 --node_score_aggregation sum --ent_score_aggregation sum
python train.py --warm_start_time 48 --emb_dim 256 128 64 32 --batch_size 128 --lr 0.0002 --dataset ICEWS18_forecasting --epoch 10 --sampling 3 --device 0 --DP_steps 3 --DP_num_edges 15 --max_attended_edges 60 --node_score_aggregation sum --ent_score_aggregation sum --ratio_update 0.75
python train.py --warm_start_time 48 --emb_dim 256 128 64 32 --batch_size 128 --lr 0.0002 --dataset YAGO1830 --epoch 10 --sampling 3 --device 0 --DP_steps 3 --DP_num_edges 15 --max_attended_edges 60 --node_score_aggregation sum --ent_score_aggregation sum --ratio_update 0.75
```
Evaluation:
```
python eval.py --load_checkpoint checkpoints_dir_name/checkpoint_name.pt --device 0
```
different num_neighbors can be specified by adding
```
--DP_num_neighbors 30 --max_attended_edges 40
```

--mongo can store configurations and results into mongodb, it's not necessary.
