
## 目录
[TOC]

## 项目简介
Baichuan2-Novel 是一个开源的网文大语言模型，本项目的目的是基于现有的开源大模型 Baichuan2 来进行领域预训练，后续如果有更好的基座会进行切换。

本项目依托于网文数据，主要进行以下几个方面的工作：
- 基于网文数据进行 Pretain，全参数微调，LoRA微调，QLoRA 等
- 支持主流的开源大模型，如 baichuan2，lamma2
- 支持 lora 与 base model 权重合并
- 模型架构优化：针对小说场景下的生成问题进行模型结构优化，致力于解决小说超长文本问题。
- 开源小说预训练数据集，指令微调数据集

基于网文发布的版本的下载链接如下表：
-------

## 环境与试用

```
pip install -r requirements.txt
```

## 项目代码介绍
- Baichuan-Pretrain: 包含了预训练的详细代码
- Baichuan-Finetune： 全参数微调的详细代码
- Baichuan-Finetune-Lora：基于 lora 进行微调的详细代码
- Baichuan-Finetune-QLora：基于 qlora 进行微调的详细代码

这几份代码都大同小异，主要是在于数据的组成方式不同，模型的加载不同等。

## 模型评估
Baichuan2-Novel 的评估主要分为两种： 
- 第一种是直接用两本没参与训练的书来计算 Rouge 分
- 第二种是采用人工评估的方式来从多个角度进行评估（待完善）。

## 模型预训练
从各方数据源中汇集了一大批小说，由于计算资源限制，从中挑选了 500+ 本小说进行预训练。
之所以进行预训练，是因为网文的表达方式与原Baichuan中的数据差别非常大，因此有必要让它学会网文的表达方式。
- 数据的具体样例如下参见: Baichuan-Pretrain/data_examples/dev.json
- 代码的运行：./ds_finetune.sh，你可以自行更改 ds_finetune.sh 中的参数

## 模型微调
微调数据是精选出 30 本小说，采用的是用小说的上一章节来预测下一章节。

### 1. 全参数微调

## 2. LoRA 微调

## 3. QLoRA 微调

