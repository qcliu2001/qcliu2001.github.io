---
layout: archive
title: "🚀 关于我"
permalink: /test/
author_profile: true
---

# Conversational Search代码复现日志

[TOC]

## **Dataset**

### **QReCC**

QReCC通过研究人工改写的查询，专注于会话场景中的查询改写问题。因此，它为每个对话轮次提供了一个理想查询。我们认为这可能并非最优选择。

#### 📑 **项目信息**

> + **原Repo（数据）：**https://github.com/apple/ml-qrecc/
> + **服务器路径：**`/home/workingplace/liuqc/datasets/conv_dataset/qrecc/`
> + **其他官方链接：**
>   + 无
> + **非官方链接：**
>   + Huggingface（语料库，数量有点对不上）：https://hf-mirror.com/datasets/namespace-Pt/qrecc-corpus

#### **🔎 数据概况**

| 类型       | 数量       | 服务器上可用路径                                             | /    | /    |
| ---------- | ---------- | ------------------------------------------------------------ | ---- | ---- |
| Train      | 63,501     | ``/home/workingplace/liuqc/datasets/conv_dataset/qrecc/qrecc_train.json`` | ✅    | 🌟    |
| Dev        | /          | /                                                            | /    | /    |
| Test       | 16,451     | `/home/workingplace/liuqc/datasets/conv_dataset/qrecc/qrecc_test.json` | ✅    | 🌟    |
| Collection | 54,573,064 |                                                              |      |      |

-----

### **TopiOCQA**

TopiOCQA聚焦于会话场景下话题切换的挑战，其对话时长比QReCC更长，因此给查询重写带来了更多困难。与QReCC不同的是，它不提供人工改写的查询。

#### 📑 **项目信息**

> + **原Repo（数据）：**https://github.com/McGill-NLP/topiocqa
> + **服务器路径：**`/home/workingplace/liuqc/datasets/conv_dataset/topiocqa/`
> + **其他官方链接：**
>   + GitHub网站：https://mcgill-nlp.github.io/topiocqa/
>   + Huggingface（语料库）：https://hf-mirror.com/datasets/McGill-NLP/TopiOCQA-wiki-corpus
>   + Huggingface（数据集）：https://hf-mirror.com/datasets/McGill-NLP/TopiOCQA
> + **非官方链接：**
>   + 无

#### **🔎 数据概况**

| 类型       | 数量       | 服务器上可用路径                                             | /    | /    |
| ---------- | ---------- | ------------------------------------------------------------ | ---- | ---- |
| Train      | 45,450     | `/home/workingplace/liuqc/datasets/conv_dataset/topiocqa/topiocqa_train.jsonl` | ✅    | 🌟    |
| Dev        | 2,514      | `/home/workingplace/liuqc/datasets/conv_dataset/topiocqa/topiocqa_valid.jsonl` | ✅    | 🌟    |
| Test       | /          | /                                                            | /    | /    |
| Collection | 25,700,592 | `/home/workingplace/liuqc/datasets/conv_dataset/topiocqa/topiocqa_corpus.jsonl` | ✅    | 🌟    |
| Collection | 25,700,592 | `/home/workingplace/liuqc/datasets/conv_dataset/topiocqa/TopiOCQA-wiki-corpus/train-*of-00027.parquet` | ✅    | /    |

##### **1. 数据格式**

```json
{
    "Context": ["when will the new dunkirk film be released on dvd", "18 December 2017"],
    "Conversation_no": 1,
    "Turn_no": 2,
    "Question": "what is this film about?",
    "is_nq": false,
    "Answer": "Dunkirk evacuation of World War II",
    "Topic": "Dunkirk (2017 film)",
    "Topic_section": "Introduction",
    "Rationale": "Dunkirk is a 2017 war film written, directed, and produced by Christopher Nolan that depicts the Dunkirk evacuation of World War II",
    "Additional_answers": [
        {
            "Answer": "It depicts the Dunkirk evacuation of World War II",
            "Topic": "Dunkirk (2017 film)",
            "Topic_section": "Introduction",
            "Rationale": "Dunkirk is a 2017 war film written, directed, and produced by Christopher Nolan that depicts the Dunkirk evacuation of World War II."
        },
        {
            "Answer": "It depicts the Dunkirk evacuation of World War II.",
            "Topic": "Dunkirk (2017 film)",
            "Topic_section": "Introduction",
            "Rationale": "Dunkirk is a 2017 war film written, directed, and produced by Christopher Nolan that depicts the Dunkirk evacuation of World War II."
        },
        {
            "Answer": "In May 1940, during the Battle of France, Allied soldiers have retreated to Dunkirk. Tommy, a young British private, is the sole survivor of a German ambush. At the beach, he finds thousands of troops awaiting evacuation and meets Gibson, who is burying a body. After a Luftwaffe dive-bomber attack, they attempt to get aboard a hospital ship, but are ordered off. The ship is sunk by dive bombers; Tommy saves another soldier, Alex. They get aboard a destroyer, only to have it torpedoed and sunk before it can depart",
            "Topic": "Dunkirk (2017 film)",
            "Topic_section": "Plot",
            "Rationale": "In May 1940, during the Battle of France, Allied soldiers have retreated to Dunkirk. Tommy, a young British private, is the sole survivor of a German ambush. At the beach, he finds thousands of troops awaiting evacuation and meets Gibson, who is burying a body. After a Luftwaffe dive-bomber attack, they attempt to get aboard a hospital ship, but are ordered off. The ship is sunk by dive bombers; Tommy saves another soldier, Alex. They get aboard a destroyer, only to have it torpedoed and sunk before it can depart."
        }
    ],
    "Gold_passage": {
        "id": "wiki:14979882",
        "title": "Dunkirk (2017 film) [SEP] Introduction",
        "text": "Dunkirk is a 2017 war film written, directed, and produced by Christopher Nolan that depicts the Dunkirk evacuation of World War II. Its ensemble cast includes Fionn Whitehead, Tom Glynn-Carney, Jack Lowden, Harry Styles, Aneurin Barnard, James D'Arcy, Barry Keoghan, Kenneth Branagh, Cillian Murphy, Mark Rylance, and Tom Hardy. The film was distributed by Warner Bros. \"Dunkirk\" portrays the evacuation from three perspectives: land, sea, and air. It has little dialogue, as Nolan sought instead to create suspense from cinematography and music. Filming began in May 2016 in Dunkirk and ended that September in Los Angeles, when post-production began. Cinematographer Hoyte van Hoytema shot the film on IMAX 65 mm and 65 mm large-format film stock."}
}
```

##### **2. 语料库格式**

```json
{
    "title": "Eliza Fletcher",
    "sub_title": "Life and works",
    "contents": "Archibald Fletcher's steady adherence to his Whig principles prevented his getting into practice, and they were often reduced to their last guinea. Her sympathy prevented her from ever regretting the sacrifice to principle. Afterwards success in life set steadily in with little interruption. Mrs Fletcher died at Lancrigg, Grasmere, on 5 February 1858.",
    "id": "wiki:4"
}
```

**3. 重要备注**

+ 原文中是有个test集的，但是官方没公开，看了一些CS的论文，里面的**实验设置都是用valid集当作test集**。
+ `topiocqa_corpus.jsonl`是由官方公开的`TopiOCQA-wiki-corpus`转过来的。

-----

## **Retriever**

### **ANCE**

#### 📑 **项目信息**

> + **原Repo（包括代码）：**https://github.com/microsoft/ANCE
> + **模型版本：**`ad-hoc-ance-msmarco`
> + **服务器路径：**`/home/workingplace/liuqc/model/ance/passage_ance_firstp_checkpoint`
> + **百度网盘路径：**`./model/Passage_ANCE_FirstP_Checkpoint.zip`
> + **官网模型链接已经失效，在GitHub issue（https://github.com/microsoft/ANCE/issues/23）中有私人的Google云盘链接**
>   + Google云盘（🌟）：https://drive.google.com/file/d/1IHqi2EpU3hdoa06LWbpoAzg21oVT7e2o/view?usp=share_link
>   + Huggingface（先用上面的链接下载模型，这个模型没验证过是否和官方一致）：https://hf-mirror.com/3ricL/ad-hoc-ance-msmarco

-----

## **Methods**

### **QuReTeC (SIGIR'2020)**

#### 📝 **论文信息**

> + **标题：**Query Resolution for Conversational Search with Limited Supervision
> + **类型：**查询重构 --> 查询扩展
> + **模型：**基于`bert-large-uncased`实现的NER模型
> + **数据：**QuAC构造远程监督数据进行训练和评估（评估重写效果），CAsT'2019进行评估（评估检索效果）

#### 📑 **项目信息**

> + **原Repo（包括代码和数据）：**https://github.com/nickvosk/sigir2020-query-resolution
> + **服务器路径：**`/home/workingplace/liuqc/project/cs_baselines/sigir2020-query-resolution`
> + **启动服务器可运行该项目的虚拟环境：**`source activate llama_factory`
> + **requirements.txt**
>
> ```
> numpy==2.3.1
> pytorch_transformers==1.2.0
> torch==2.7.0
> ```

##### **1. 训练和评估**

已经将单机单卡的训练代码整理为文件`run_ner_single_gpu.py`中，通过`train_ner_single_gpu.sh`即可启动训练。

```bash
## train_ner_single_gpu.sh
BASE_DIR=./models/  
DATA_DIR=./data/quac_canard/token_classification/
BERT_MODEL=/home/workingplace/liuqc/project/cs_baselines/sigir2020-query-resolution/models/bert-large-uncased
TRAIN_ON=train_gold_supervision
DEV_ON=dev_gold_supervision

MODEL_ID=250625_03 # 对模型进行命名，将在./models目录下创建该模型的目录，如./models/250625_03

# CUDA_VISIBLE_DEVICES只能指定一张显卡，如果指定多张需要使用DP或DDP
# DP或DDP并未在run_ner_single_gpu.py中实现，需要通过my_run_ner.py启动训练
# 以下参数设置参考了论文开源的模型191790_50中的train_args.json
CUDA_VISIBLE_DEVICES="4" python -m run_ner_single_gpu \
--task_name ner \
--bert_model $BERT_MODEL \
--max_seq_length 300 \
--train_batch_size 4 \
--learning_rate 3e-05 \
--num_train_epochs 20 \
--warmup_proportion 0.3 \
--hidden_dropout_prob 0.4 \
--train_on $TRAIN_ON \
--do_train \
--data_dir $DATA_DIR \
--base_dir $BASE_DIR \
--model_id $MODEL_ID \
--dev_on $DEV_ON
```

文章中混合远程监督数据和黄金数据进行训练，采用多阶段的训练方法，通过`train_ner_single_gpu.sh`即可重启下一阶段训练。

```bash
BASE_DIR=./models/  
DATA_DIR=./data/quac_canard/token_classification/
BERT_MODEL=/home/workingplace/liuqc/project/cs_baselines/sigir2020-query-resolution/models/bert-large-uncased
TRAIN_ON=train_gold_supervision
DEV_ON=dev_gold_supervision

MODEL_ID=250626_01  # provide an ID for the model to be trained here.
PRETRAINED_MODEL_ID=250625_03

CUDA_VISIBLE_DEVICES="4" python -m run_ner_single_gpu \
--task_name ner \
--max_seq_length 300 \
--train_batch_size 4 \
--learning_rate 3e-05 \
--num_train_epochs 20 \
--warmup_proportion 0.3 \
--hidden_dropout_prob 0.4 \
--retrain_on $TRAIN_ON \
--do_train \
--data_dir $DATA_DIR \
--base_dir $BASE_DIR \
--model_id $MODEL_ID \
--pretrained_model_id $PRETRAINED_MODEL_ID \
--dev_on $DEV_ON
```

对查询重写的评估（评估扩展查询和黄金查询）通过`evaluate_ner_cpu.sh`启动。

```bash
BASE_DIR=./models/
# model trained on QuAC gold resolutions (as in paper)
BERT_MODEL=/home/workingplace/liuqc/project/cs_baselines/sigir2020-query-resolution/models/250626_01
MODEL_ID=250626_01

DATA_DIR=./data/quac_canard/token_classification/
DEV_ON=test_gold_supervision
 
python -m run_ner_single_gpu \
--task_name ner \
--bert_model $BERT_MODEL \
--do_eval \
--do_lower_case \
--data_dir $DATA_DIR \
--base_dir $BASE_DIR \
--dev_on $DEV_ON \
--model_id $MODEL_ID \
--no_cuda  # 可以直接不加，会快很多，但不能指定显卡，一指定就报错
```

##### **2. 可用的模型**

| #    | 相对路径                      |                                                              |
| ---- | ----------------------------- | ------------------------------------------------------------ |
| 1    | `./models/bert-large-uncased` | Google开源的预训练模型，没在特定任务上微调过，不能直接使用，只能作为模型训练的初始化基座 |
| 2    | `./models/191790_50`          | 论文开源的训练好的模型，性能和论文中的数据基本一致           |

##### **3. 重要备注**

+ 关于**单机多卡**，模型在一张3090上显存占用为8691MiB（共24576MiB），<u>无需单机多卡</u>。如果使用单机多卡，如：DP或DDP，反而时延较严重，可能来自于GPU间通信，且需要存储的中间量变多。
+ 关于较为详细的**代码注释**，可以参考`my_run_ner.py`，里面包括<u>单机多卡两种形式</u>的代码，也有各部分（如模型）的重要注释。
+ 通过**BERT实现NER任务**涉及到<u>token和word不一致</u>的情况，会在代码中导致`input_ids`和`labels`对不齐，代码实现会通过`valid`来实现对齐、计算损失。比如对于`"New York"`，假设tokenize后为`["New", "Yor", "##k"]`，这样计算损失的时候，只考虑`"Yor"`。
+ <u>项目中只提供了训练和评估重写模型的代码</u>，如果需要评估检索性能，需要用重写后的查询自己检索并评估。

-----

## **其他资料**

### **常用链接**

+ **综述：**https://github.com/fengranMark/ConvSearch-Survey

### **常用指令**

#### **1. 本地传输文件到服务器**

```shell
scp -r -P 22000 Passage_ANCE_FirstP_Checkpoint.zip liuqc@59.77.5.112:/home/workingplace/liuqc/model/ance
```
