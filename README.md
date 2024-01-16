# SheepDog_reproduce

This repository contains the **gossipcop** dataset and its extended dataset **gossipcop_SheepDog_chatglm**.

You can download the datasets from [Google Drive](https://drive.google.com/file/d/1a1gIVwLb-BvzomRHmFzXzGRLNHvbrEHY/view?usp=drive_link). Then put them into data folder and unzip them. 

# Overview

The **gossipcop** dataset is from [FakeNewsNet](https://github.com/KaiDMML/FakeNewsNet?tab=readme-ov-files). 
It is a subset of the original dataset, which only contains the news articles.

The **gossipcop_SheepDog_chatglm** dataset is an extended version of the **gossipcop** dataset, following the steps from the paper [Fake News in Sheep's Clothing: Robust Fake News Detection Against LLM-Empowered Style Attacks](https://arxiv.org/abs/2310.10830) (SheepDog).

**SheepDog** presents the style-related vulnerability of state-of-the-art text-based fake news detectors to LLM-empowered style attacks. 
It also proposes a style-agnostic fake news detector, which is robust against LLM-empowered style attacks.

## Dataset Structure

```
.
├── LICENSE
├── README.md
├── data
├── data_example
│   ├── gossipcop_SheepDog_chatglm_8k_example
│   │   ├── fake
│   │   │   └── gossipcop-13736481
│   │   │       ├── news content.json
│   │   │       ├── reliable.txt
│   │   │       ├── style_attack.txt
│   │   │       ├── unreliable.txt
│   │   │       ├── veracity_attributions.txt
│   │   │       ├── veracity_attributions_reliable.txt
│   │   │       └── veracity_attributions_unreliable.txt
│   │   └── real
│   │       └── gossipcop-736743
│   │           ├── news content.json
│   │           ├── reliable.txt
│   │           ├── style_attack.txt
│   │           ├── unreliable.txt
│   │           ├── veracity_attributions.txt
│   │           ├── veracity_attributions_reliable.txt
│   │           └── veracity_attributions_unreliable.txt
│   └── gossipcop_example
│       ├── fake
│       │   └── gossipcop-13736481
│       │       └── news content.json
│       └── real
│           └── gossipcop-736743
│               └── news content.json
└── structure.txt

13 directories, 21 files

```

# LLM-Empowered News Reframing

Contains 3 types of news reframing tasks: style attack, style reframing, and veracity attribution.

## Style Attack

```
Rewrite the following article using the style of [publisher name]: [news article]
```

Two selections for the publisher name:

1. National Enquirer
2. The New York Times

National Enquirer is a tabloid, which is used to camouflage real news. The New York Times is a reliable news source, which is used to camouflage fake news.

## Style Reframing

```
Rewrite the following article in a / an [specified] tone: [news article]
```

Four general style-oriented adjectives for the prompt.
Two for reliable style:

1. objective and professional
2. neutral

Two for unreliable style:

1. emotionally triggering
2. sensational

## Veracity Attributions

```
Article: [news article] Question: Which of the following problems does this article have? Lack of credible sources, False or misleading information, Biased opinion, Inconsistencies with reputable sources. If multiple options apply, provide a commaseparated list ordered from most to least related. Answer "No problems" if none of the options apply.
```

# Reference

If you use this code, please cite the following paper:

```
@article{shu2018fakenewsnet,
  title={FakeNewsNet: A Data Repository with News Content, Social Context and Dynamic Information for Studying Fake News on Social Media},
  author={Shu, Kai and  Mahudeswaran, Deepak and Wang, Suhang and Lee, Dongwon and Liu, Huan},
  journal={arXiv preprint arXiv:1809.01286},
  year={2018}
}
```
```
@misc{wu2023fake,
      title={Fake News in Sheep's Clothing: Robust Fake News Detection Against LLM-Empowered Style Attacks}, 
      author={Jiaying Wu and Bryan Hooi},
      year={2023},
      eprint={2310.10830},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```