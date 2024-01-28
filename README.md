## Baseline models
### Embedding models
We used DGL-KE to train the embedding models.
```
# TransE
python -m dglke.train --model_name TransE_l2 --dataset OBL2021 \ 
       --batch_size 2048 --neg_sample_size 1024 --hidden_dim 360 \
       --gamma 8.0 --lr 0.1 --max_step 550000 --log_interval 1000 \
       --batch_size_eval 512 --regularization_coef 3.00E-09 -rn 3 -adv -a 1.0
	   
# DistMult
python -m dglke.train --model_name DistMult --dataset OBL2021 \
       --batch_size 2048 --neg_sample_size 1024 --hidden_dim 380 \
       --lr 0.15 --max_step 950000 --log_interval 1000 \
       --batch_size_eval 128 --regularization_coef 4.00E-07 -rn 3 -adv -a 1.0

# ComplEx
python -m dglke.train --model_name ComplEx --dataset OBL2021 \
       --batch_size 1024 --neg_sample_size 512 --hidden_dim 380 \
       --lr 0.1 --max_step 800000 --log_interval 1000 \
       --batch_size_eval 512 --regularization_coef 2.00E-06 -rn 3 -adv -a 1.0
```

### Rule-based models
- The source code we used to build AnyBURL is saved in https://drive.google.com/drive/folders/1bQXP-tetV0si9YMA1ASd8HV1mDOph61p?usp=sharing, in /AnyBURL-RE folder.
- The source code we used to infer predictions is saved in the same link, in /SAFRAN folder.
- Rules generated by AnyBURL is saved as rules-1000 file in current directory.

## Code
- The implementation is in code.ipynb file with introduction. 
- The embedding files generated by baseline models are needed to run the code, the embeddings data is saved in https://drive.google.com/drive/folders/1bQXP-tetV0si9YMA1ASd8HV1mDOph61p?usp=sharing, in /ckpts folder. Put the entire folder in MSc_project_2597630w directory.
- Predictions we got from the trained models and used in the experiment are saved in /pred fold in currect directory.

## Cite

```
@inproceedings{DGL-KE,
author = {Zheng, Da and Song, Xiang and Ma, Chao and Tan, Zeyuan and Ye, Zihao and Dong, Jin and Xiong, Hao and Zhang, Zheng and Karypis, George},
title = {DGL-KE: Training Knowledge Graph Embeddings at Scale},
year = {2020},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
booktitle = {Proceedings of the 43rd International ACM SIGIR Conference on Research and Development in Information Retrieval},
pages = {739–748},
numpages = {10},
series = {SIGIR '20}
}
```

```
@article{10.1093/bioinformatics/btaa274,
    author = {Breit, Anna and Ott, Simon and Agibetov, Asan and Samwald, Matthias},
    title = "{OpenBioLink: a benchmarking framework for large-scale biomedical link prediction}",
    journal = {Bioinformatics},
    volume = {36},
    number = {13},
    pages = {4097-4098},
    year = {2020},
    month = {04},
    issn = {1367-4803},
    doi = {10.1093/bioinformatics/btaa274},
    url = {https://doi.org/10.1093/bioinformatics/btaa274},
    eprint = {https://academic.oup.com/bioinformatics/article-pdf/36/13/4097/33458979/btaa274.pdf},
}
```

```
@inproceedings{SAFRAN,
    title={{SAFRAN}: An interpretable, rule-based link prediction method outperforming embedding models},
    author={Simon Ott and Christian Meilicke and Matthias Samwald},
    booktitle={3rd Conference on Automated Knowledge Base Construction},
    year={2021},
    url={https://openreview.net/forum?id=jCt9S_3w_S9},
}
```

```
@inproceedings{anyburl,
	title={Anytime Bottom-Up Rule Learning for Knowledge Graph Completion},
	isbn={978-0-9992411-4-1},
	url={https://www.ijcai.org/proceedings/2019/435},
	doi={10.24963/ijcai.2019/435},
	eventtitle={Twenty-Eighth International Joint Conference on Artificial Intelligence \{{IJCAI}-19\}},
	pages={3137--3143},
	booktitle={Proceedings of the Twenty-Eighth International Joint Conference on Artificial Intelligence},
	publisher={International Joint Conferences on Artificial Intelligence Organization},
	author={Meilicke, Christian and Chekol, Melisachew Wudage and Ruffinelli, Daniel and Stuckenschmidt, Heiner},
	year={2019},
	date={2019-08},
}
```