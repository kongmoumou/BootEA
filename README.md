# BootEA
Source code and datasets for IJCAI-2018 paper "_[Bootstrapping Entity Alignment with Knowledge Graph Embedding](https://www.ijcai.org/proceedings/2018/0611.pdf)_".

## TODO

- [ ] 数据说明
- [ ] run
- [ ] 补充注释
- [ ] demo

## Dataset
We use two datasets, namely DBP15K and DWY100K. DBP15K can be found [here](https://github.com/nju-websoft/JAPE) while DWY100K is as follows.
### Id files of DWY100K
Folder "dataset/DWY100K/" contains the id files of DWY100K. 

The subfolder "mapping/0_3" contains the id files used in BootEA and MTransE while the subfolder "sharing/0_3" is for JAPE and IPTransE. The two datasets use 30% reference entity alignment as seeds. Id files in "sharing/0_3" are generated following the idea of parameter sharing that lets the two aligned enitites in seed alignment share the same id, while "mapping/0_3" does not.

The subfolder "mapping/0_3" inculdes the following files:
* ent_ids_1: entity ids in the source KG;
* ent_ids_2: entity ids in the target KG;
* ref_ent_ids: entity alignment for testing, list of pairs like (e_s \t e_t);
* sup_ent_ids: seed entity alignment (training data);
* rel_ids_1: relation ids in the source KG;
* rel_ids_2: relation ids in the target KG;
* triples_1: relation triples in the source KG;
* triples_2: relation triples in the target KG;

The subfolder "sharing/0_3" inculdes the following additional files:
* attr_ids_1: attribute ids in the source KG;
* attr_ids_2: attribute ids in the target KG;
* attr_range_type_1: attribute ranges in the source KG, list of pairs like (attribute id \t range code);
* attr_range_type_2: attribute ranges in the target KG;
* ent_attrs_1: entity attributes in the source KG; 
* ent_attrs_2: entity attributes in the target KG; 
* ref_ents: seed entity alignment denoted by URIs (training data);

### Raw data of DWY100K
File "dataset/DWY100K_raw_data.zip" is the raw data of DWY100K, where each entity, relation or attribute is represented by a URI. Each dataset has the following files:

* ent_links: all the entity links without traning/test splits;
* triples_1: relation triples in the source KG, list of triples like (h \t r \t t);
* triples_2: relation triples in the target KG;
* attr_triples_1: attribute triples in the source KG;
* attr_triples_2: attribute triples in the target KG;
* uri_attr_range_type_1: attribute ranges in the source KG, list of pairs like (attribute uri \t range code);
* uri_attr_range_type_2: attribute ranges in the target KG;
* attrs_1: entity attributes in the source KG; 
* attrs_2: entity attributes in the target KG; 

## Code
Folder "code" contains all codes of BootEA, in which:
* "AlignE.py" is the implementation of AlignE;
* "BootEA.py" is the implementation of BootEA;
* "param.py" is the config file.

### Dependencies
* Python 3
* Tensorflow 1.x 
* Scipy
* Numpy
* Graph-tool or igraph or NetworkX

If you fail to install Graph-tool, we suggest you to set "self.heuristic = False" in param.py, which allows BootEA to run using igraph rather than Graph-tool. If you have trouble installing igraph, you can use NetworkX by modifying the code of line 186-189 in train_bp.py and replacing "mwgm_graph_tool" and "mwgm_igraph" with "mwgm_networkx". Note that, igraph and NetworkX are much slower than Graph-tool!

> If you have any difficulty or question in running code and reproducing experiment results, please email to zqsun.nju@gmail.com and whu@nju.edu.cn.

## Citation
If you use this model or code, please cite it as follows:      
```
@inproceedings{BootEA,
  author    = {Zequn Sun and Wei Hu and Qingheng Zhang and Yuzhong Qu},
  title     = {Bootstrapping Entity Alignment with Knowledge Graph Embedding},
  booktitle = {IJCAI},
  pages     = {4396--4402},
  year      = {2018}
}
```

## Links
The following links point to some recent work that uses our datasets:
 
* Yixin Cao, et al. [Multi-Channel Graph Neural Network for Entity Alignment.](https://www.aclweb.org/anthology/P19-1140) In: ACL 2019.  
* Qiannan Zhu, et al. [Neighborhood-Aware Attentional Representation for Multilingual Knowledge Graphs.](https://www.ijcai.org/proceedings/2019/0269.pdf) In: IJCAI 2019.  
* Qingheng Zhang, et al. [Multi-view Knowledge Graph Embedding for Entity Alignment.](https://www.ijcai.org/proceedings/2019/0754.pdf) In: IJCAI. 2019.  
* Tingting Jiang, et al. [Two-Stage Entity Alignment: Combining Hybrid Knowledge Graph Embedding with Similarity-Based Relation Alignment.](https://link.springer.com/chapter/10.1007/978-3-030-29908-8_13) In: PRICAI 2019.  
