# BootEA
Source code and datasets for IJCAI-2018 paper "_[Bootstrapping Entity Alignment with Knowledge Graph Embedding](https://www.ijcai.org/proceedings/2018/0611.pdf)_".

## TODO

- [ ] 数据说明
- [ ] run
- [ ] 补充注释
- [ ] demo

## Dataset

我们使用了两个数据集，DBP15K 和 DWY100K。DBP15K 可以[在此获取](https://github.com/nju-websoft/JAPE)。DWY100K 如下所示。

### Id files of DWY100K

文件夹 `dataset/DWY100K/` 包含 DWY100K 的 id files

子文件夹 `mapping/0_3` 包含 BootEA 和 MTransE 的 id files。
子文件夹 `sharing/0_3` 包含 JAPE 和 IPTransE 的 id files。
两个数据集使用 **30%** 作为种子对齐。

`sharing/0_3` 使用 parameter sharing 方法让对齐实体共享 id。
`mapping/0_3` 则没有这样做。

`mapping/0_3` 包含以下文件
* ent_ids_1: 来源 KG 的 entity ids;
* ent_ids_2: 目标 KG 的 entity ids;
* ref_ent_ids: 用于测试的对齐对，如 (e_s \t e_t);
* sup_ent_ids: 种子对齐 (训练数据);
* rel_ids_1: 来源 KG 的 relation ids;
* rel_ids_2: 目标 KG 的 relation ids;
* triples_1: 来源 KG 的 relation triples（三元组在）;
* triples_2: 目标 KG 的 relation triples（三元组在）;

`sharing/0_3` 额外包含以下附加文件
* attr_ids_1: 来源 KG 的 attribute ids;
* attr_ids_2: 目标 KG 的 attribute ids;
* attr_range_type_1: 来源 KG 的属性范围（attribute ranges）, 如 (attribute id \t range code);
* attr_range_type_2: 目标 KG 的属性范围（attribute ranges）;
* ent_attrs_1: 来源 KG 的实体属性entity attributes; 
* ent_attrs_2: 目标 KG 的实体属性entity attributes; 
* ref_ents: 用 URIS 表示的种子对齐(训练数据);

### DWY100K 的原始数据
`dataset/DWY100K_raw_data.zip` 是 DWY100K 的原始数据, 其中每个实体、关系或属性都用URI 表示。每个数据集包含以下文件:

* ent_links: 所有实体连接（不区分训练/测试集）;
* triples_1: 来源 KG 的关系三元组，如 (h \t r \t t);
* triples_2: 目标 KG 的关系三元组;
* attr_triples_1: 来源 KG 的属性三元组;
* attr_triples_2: 目标 KG 的属性三元组;
* uri_attr_range_type_1: 来源 KG 的属性范围（attribute ranges）, 如 (attribute uri \t range code);
* uri_attr_range_type_2: 来源 KG 的属性范围（attribute ranges）;
* attrs_1: 来源 KG 的实体属性; 
* attrs_2: 目标 KG 的实体属性; 

## 代码
`code` 文件夹包含BootEA的所有代码, in which:
* `AlignE.py` 实现了AlignE（无迭代）;
* `BootEA.py` 实现了BootEA;
* `param.py` 配置文件.

### 依赖（TODO: 补充版本）
* Python 3
* Tensorflow 1.x 
* Scipy
* Numpy
* Graph-tool or igraph or NetworkX

如果你安装 `Graph-tool` 失败， 我们建议你设置 `self.heuristic = False` 在 `param.py` 中，这允许BootEA在运行时使用 `igraph` 而不是 `Graph-tool`。如果你安装`igraph`遇到了麻烦，你可以使用 `NetworkX` 并修改 `train_bp.py` 的 **186-189** 行（使用mwgm_networkx替换mwgm_graph_tool和 mwgm_igraph）。请注意igraph 和 NetworkX 比Graph-tool慢得多。

> 如果你运行和复现实验结果时遇到了任何困难，请发email给 zqsun.nju@gmail.com 和 whu@nju.edu.cn

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
