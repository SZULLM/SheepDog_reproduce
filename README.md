# SheepDog_reproduce

This repository contains 2 datasets：

1. `gossipcop`: contains news contents with labels (real/fake), collected from a fact-checking website Gossipcop.
2. `gossipcop_SheepDog_chatglm_8k`: an extended version of the `gossipcop` dataset, contains LLM-generated information
   about the news contents.

You can download the datasets
from [Google Drive](https://drive.google.com/file/d/1a1gIVwLb-BvzomRHmFzXzGRLNHvbrEHY/view?usp=drive_link).

# Table of Content

1. [Overview](#overview)
   2. [Dataset Size](#dataset-size)
   3. [Dataset Source](#dataset-source)
2. [Introduction](#introduction)
    1. [`gossipcop` Dataset](#gossipcop-dataset)
        1. [Dataset Structure](#dataset-structure)
        2. [Example](#example)
    2. [`gossipcop_SheepDog_chatglm_8k` Dataset](#gossipcop_sheepdog_chatglm_8k-dataset)
        1. [Dataset Structure](#dataset-structure-1)
        2. [Style Attack](#style-attack)
        3. [News Reframing](#news-reframing)
        4. [Veracity Attribution](#veracity-attribution)
3. [Dataset Example inside this Repository](#dataset-example-inside-this-repository)
4. [Reference](#reference)

# Overview

## Dataset Size

|            Dataset            | # of news articles | # of fake news articles | # of real news articles |
|:-----------------------------:|:------------------:|:-----------------------:|:-----------------------:|
|           gossipcop           |       19708        |          4717           |          14991          |
| gossipcop_SheepDog_chatglm_8k |        8000        |          4000           |          4000           |

## Dataset Source

- `gossipcop`:  Paper [FakeNewsNet](https://arxiv.org/abs/1809.01286);
  Github [link](https://github.com/KaiDMML/FakeNewsNet)
- `gossipcop_SheepDog_chatglm_8k`: Paper [SheepDog](https://arxiv.org/abs/2310.10830);

SheepDog does not release the code and dataset. We use the method proposed in the paper to generate the dataset.

# Introduction

## `gossipcop` Dataset

### Dataset Structure

```text
├── gossipcop
│   ├── fake
│   │   ├── gossipcop-13736481
│   │	│	└── news content.json
│   │	└── ....			
│   └── real
│       ├── gossipcop-841804
│       │      	└── news content.json
│	└── ....
```

`fake` folder contains all fake news. `real` folder contains all real news.

Each news has a folder named by the news id, such as `gossipcop-13736481`.

Each news folder contains a file `news content.json`, contains the meta information, such as url, text, images, etc.

### Example

`news content.json` from `fake/gossipcop-13736481`

```json
{
  "url": "https://web.archive.org/web/20180312204214/https://www.cheatsheet.com/health-fitness/how-kylie-jenner-lost-weight-post-pregnancy.html/",
  "text": "After nine months of fan speculation and hiding from the spotlight, Kylie Jenner finally revealed baby Stormi to the world. Like most celebrities, we expected Kylie to get back into shape quickly with a healthy diet and exercise. But recent photos reveal just how fast she dropped the pounds — and we’re all wondering if it’s healthy.\n\nSo, what’s Kylie’s weight-loss secret? Here’s how she managed to lose a reported 25 pounds in just two weeks.\n\n1. Kylie allegedly follows Kim K’s advice and eats super clean\n\nDuring her pregnancy, Kylie admitted to having an obsession with In-N-Out fast food, Insider notes. That’s a serious departure from the way she currently eats, however. And thanks to Kim Kardashian, Kylie is getting serious one-on-one advice on how to drop excess fat and get into shape fast post-pregnancy.\n\nThe Independent says one source added Kim advised Kylie to stick to a strict 1,500 calorie-a-day diet. Along with that, Kim suggests Kylie eats no carbs or sugar, even despite her “addiction” to fast food.\n\nNext: Kylie has been a fan of this dangerous weight-loss method for awhile.\n\n2. She may be a fan of ‘detox teas’\n\nOne source says in addition to a very strict diet, Kylie is drinking “detox teas” to help drop pounds, says HollywoodLife.com. This wouldn’t be Kylie’s first attempt at weight loss with these teas, either. She posted a photo of her holding two of her favorite detox formulas on Instagram and promoting their cleansing effects.\n\nHere’s the problem, though: Teas don’t actually have the ability to “detox” your body. And drinking them won’t automatically help you lose weight, either, though some do have a laxative effect. In this case, you’ll just lose water weight.\n\nNext: This is how Kylie prefers to train.\n\n3. When she works out, she’s sure to incorporate weight training\n\nThough sister Khloe has accused Kylie of not putting much work into her body in the past, those days are seemingly over for the young Jenner. HollywoodLife.com notes one insider reveals the new mom hits the gym for a mix of cardio and weight lifting. She’s reportedly a big fan of running, squats, and push-ups to get that pre-baby body back.\n\nThe insider also says Kylie works out with a personal trainer five days a week for up to three hours a day. If this is the case, she could be leading up to serious burnout in the future, which can hinder her results in the long run.\n\nNext: Could it be true that Kylie is sticking to a diet this low in calories?\n\n4. Kylie sticks to an extremely calorie-restricted diet, some sources say\n\nKim might advise a 1,500 calorie-a-day diet, but could Kylie be going to even bigger extreme? The Inquisitr says one insider mentions Kylie’s eating as little as 1,000 calories a day. They also said sometimes the starlet will just eat soup in the early evening as a meal replacement. And of course, this combined with no carbs or sugary sweets is sure to cause massive weight loss, even if it’s not sustainable.\n\nThe source says it gets even more severe than this, too. Allegedly, Kylie bans anyone from eating junk food around her so she’s not tempted.\n\nNext: Kylie might go overboard quickly with her regimen.\n\n5. Some say she wants to look even thinner than she did pre-pregnancy\n\nInStyle explains pre-pregnancy, Kylie was around 136 pounds, which is perfect for her 5-foot-6 frame. During her pregnancy, however, she gained upwards of 50 pounds. And now, the Inquisitr notes one source says she wants to be even thinner than she was before baby Stormi was ever in the picture.\n\nRush reports Kylie was right in the “normal” weight range at 136, so she shouldn’t aim to go too far under this number. We’ll have to see how extreme she goes with her regimen — though hopefully she’ll make healthy adjustments.\n\nNext: Some think this is the reason Kylie’s losing weight so quickly.\n\n6. Others say the weight is falling off naturally due to genetics\n\nIs it possible Kylie’s not really partaking in extreme dieting after all, and the weight is falling off due to good genes? That’s what one source tells HollywoodLife.com. They told the publication that “her biggest weight loss secret is breastfeeding and good genetics. She has always had a great metabolism and breastfeeding has kicked it into high gear.”\n\nCould it be true that the young Jenner isn’t going to any extremes after all? Maybe so. And for more drama, the source also mentions Kim’s jealous the pounds are coming off so easily for Kylie after her own personal struggles with baby weight.\n\nNext: Should Kylie lose weight this fast? Experts weigh in.\n\n7. Here’s what medical experts believe Kylie should be doing post-pregnancy\n\nDr. Elizabeth Ward tells WebMD all about weight gain and loss before and after pregnancy. Ward says a woman at an average weight should expect to gain between 25 and 35 pound, and they should also work to lose that excess weight after a year of having the baby. For at least six weeks postpartum, however, she suggests focusing on a healthy diet instead of cutting calories.\n\nWard also warns new mothers against following celebrity fad diets to lose weight quickly. Good nutrition, sleep, and physical activity are all vital for keeping energy levels up to take care of a newborn. And restricting calories if you’re a nursing mom will affect breast milk quality.\n\nCheck out The Cheat Sheet on Facebook!",
  "images": [
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/03/Two-cups-of-expresso-surrounded-by-coffee-beans-300x200.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/10/kylie-jenner-prabal-gurung-333x500.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/10/Prince-Charles-and-Princess-Diana-Wedding-Photo-300x200.png?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/01/Brad-Pitt-and-Angelina-Jolie-300x200.png?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2016/05/Woman-Running-Outdoors-300x200.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.bizographics.com/collect/?pid=4708&fmt=gif",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2014/03/warren-buffett2-640x429-300x200.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/02/Kim-Kylie-Chicago-nursery-640x360.png?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/03/Kylie-Jenner-mirrr-selfie.png?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/01/Kate-and-William-1-300x200.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://amplifypixel.outbrain.com/pixel?mid=0034bb066d42696be38e2f3f9e15a0d462",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/09/GettyImages-178667140-300x200.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/03/Kylie-Jenner-mirror-selfie-in-her-bathroom-587x500.png?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/03/Brittany-Maynard-2-300x200.png?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/03/Expecting-baby-640x426.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.facebook.com/tr?id=1447317708679797&ev=PageView&noscript=1",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/03/Kylie-Jenner-teatox-609x500.png?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/02/kylie-jenner-stormi-duo-640x453.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/10/melania-gardening-balmain-300x200.jpg?x90866",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/02/Kim-Kylie-Chicago-nursery-640x360.png",
    "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2016/10/Insomnia-300x200.jpg?x90866",
    "data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="
  ],
  "top_img": "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/02/Kim-Kylie-Chicago-nursery-640x360.png",
  "keywords": [],
  "authors": [
    "Lauren Weiler"
  ],
  "canonical_link": "https://web.archive.org/web/20180312204214/https://www.cheatsheet.com/health-fitness/how-kylie-jenner-lost-weight-post-pregnancy.html/?a=viewall",
  "title": "Kylie Jenner Has Lost a Startling Amount of Weight Post-Pregnancy, and Here’s How",
  "meta_data": {
    "viewport": "width=device-width, initial-scale=1, user-scalable=yes",
    "google-site-verification": "ktiOxQqv9Xlcn7qytDrsOVw_-MQ9S7bo2G5Iyfu-I9M",
    "apple-mobile-web-app-capable": "yes",
    "apple-mobile-web-app-title": "The Cheat Sheet",
    "robots": "NOODP,NOYDIR",
    "syndication-source": "https://www.cheatsheet.com/health-fitness/how-kylie-jenner-lost-weight-post-pregnancy.html/",
    "p": {
      "domain_verify": "936edf149ecbc3171d89b1f25f05e153"
    },
    "description": "After Kylie Jenner had baby Stormi, fans freaked out about her sudden weight loss. Here's how she lost the weight so quickly.",
    "og": {
      "locale": "en_US",
      "type": "article",
      "title": "Kylie Jenner Has Lost a Startling Amount of Weight Post-Pregnancy, and Here's How",
      "description": "After Kylie Jenner had baby Stormi, fans freaked out about her sudden weight loss. Here's how she lost the weight so quickly.",
      "url": "https://web.archive.org/web/20180312204214/https://www.cheatsheet.com/health-fitness/how-kylie-jenner-lost-weight-post-pregnancy.html/?a=viewall",
      "site_name": "The Cheat Sheet",
      "image": {
        "identifier": "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2017/03/Expecting-baby-640x426.jpg",
        "secure_url": "https://www.cheatsheet.com/wp-content/uploads/2017/03/Expecting-baby-640x426.jpg"
      }
    },
    "article": {
      "publisher": "https://www.facebook.com/wallstcheatsheet",
      "tag": "pregnancy",
      "section": "Health & Fitness",
      "published_time": "2018-03-06T17:44:17-04:00"
    },
    "fb": {
      "app_id": 534706763367100,
      "admins": 826582091
    },
    "twitter": {
      "card": "summary_large_image",
      "description": "After Kylie Jenner had baby Stormi, fans freaked out about her sudden weight loss. Here's how she lost the weight so quickly.",
      "title": "Kylie Jenner Has Lost a Startling Amount of Weight Post-Pregnancy, and Here's How",
      "site": "@cheatsheet",
      "image": "https://web.archive.org/web/20180312204214im_/https://www.cheatsheet.com/wp-content/uploads/2018/02/Kim-Kylie-Chicago-nursery-640x360.png",
      "creator": "@cheatsheet"
    },
    "generator": "WordPress 4.9.4",
    "sailthru.date": "2018-03-06 17:44:17",
    "sailthru.tags": "health-fitness,relationships-family,celebrities,Kim Kardashian,Kylie jenner",
    "sailthru.author": "lauren-w",
    "sailthru.image.full": "https://www.cheatsheet.com/wp-content/uploads/2018/03/Kylie-Jenner-mirror-selfie-in-her-bathroom.png",
    "sailthru.image.thumb": "https://www.cheatsheet.com/wp-content/uploads/2018/03/Kylie-Jenner-mirror-selfie-in-her-bathroom-150x100.png",
    "position": 2
  },
  "movies": [],
  "publish_date": 1.520372657E9,
  "source": "https://web.archive.org",
  "summary": ""
}
```

## `gossipcop_SheepDog_chatglm_8k` Dataset

### Dataset Structure

```text
├── gossipcop_SheepDog_chatglm_8k
│   ├── fake
│   │   ├── gossipcop-13736481
│   │	│	├── news content.json
│   │	│	├── reliable.txt
│   │	│	├── style_attack.txt
│   │	│	├── unreliable.txt
│   │	│	├── veracity_attributions.txt
│   │	│	├── veracity_attributions_reliable.txt
│   │	│	└── veracity_attributions_unreliable.txt
│   │	└── ....
│   └── real
│       ├── gossipcop-841804
│       │      	├── news content.json
│       │      	├── reliable.txt
│       │      	├── style_attack.txt
│       │      	├── unreliable.txt
│       │      	├── veracity_attributions.txt
│       │      	├── veracity_attributions_reliable.txt
│       │      	└── veracity_attributions_unreliable.txt
│	└── ....
```        

`gossipcop_SheepDog_chatglm_8k` Dataset has the same structure as the `gossipcop` dataset.

In addition, each news folder contains 6 extra files:

1. `style_attack.txt`
2. `reliable.txt`
3. `unreliable.txt`
4. `veracity_attributions.txt`
5. `veracity_attributions_reliable.txt`
6. `veracity_attributions_unreliable.txt`

`style_attack.txt` is used for illustrating the **style attack** to fake news detectors.

The rest 5 files are used for training a model that is robust against the style attack. SheepDog proposes two methods
to generate the 5 files:

1. **News Reframing**
2. **Veracity Attribution**

### Style Attack

Idea: rewrite the news in different styles:

1. For `real` news, rewrite in `National Enquirer` style.
2. For `fake` news, rewrite in `The New York Times` style.

#### Prompt

```
Rewrite the following article using the style of [publisher name]: [news article]
```

#### Example

`style_attack.txt` from `fake/gossipcop-13736481

```text
Kylie Jenner has finally revealed the arrival of her baby, Stormi, to the world after keeping her pregnancy under wraps for nine months. While many expected the reality star to quickly bounce back into shape with a healthy diet and exercise regimen, recent photos suggest that she has lost a significant amount of weight, leaving fans to wonder if it's healthy.

So, what's Kylie's secret to losing 25 pounds in just two weeks? According to various sources, the Keeping Up with the Kardashians star is following in the footsteps of her sister, Kim Kardashian, and is eating a super-strict diet that involves eating only 1,500 calories per day and avoiding carbs and sugar, even though she has a reported addiction to In-N-Out fast food.

In addition to her diet, Kylie is also said to be drinking "detox teas" to help her drop pounds. However, experts warn that teas do not actually have the ability to "detox" the body and that drinking them will not necessarily help you lose weight.

Kylie is also said to be incorporating weight training into her workout routine, which is a good way to burn calories and build muscle. However, working out too much can lead to burnout, which can hinder weight loss results in the long run.

There are also rumors that Kylie is sticking to an extremely calorie-restricted diet, with some sources claiming that she is eating as little as 1,000 calories per day. However, experts suggest that this is not a healthy approach to weight loss and that new mothers should focus on a healthy diet instead of cutting calories.

Finally, some sources suggest that Kylie's weight loss may be due to good genetics and breastfeeding, rather than extreme dieting. While it is possible that Kylie is not going to any extremes after all, it is important for new mothers to focus on good nutrition, sleep, and physical activity to keep energy levels up and maintain a healthy weight.
```

Two selections for the publisher name:

1. National Enquirer
2. The New York Times

`National Enquirer` is a tabloid, which is an unreliable news source, while `The New York Times` is a reliable news
source

### News Reframing

Idea: rewrite the news in different styles, and then feed the model with the original version, the reliable version and
the unreliable version.
Force the model to focus on the content of the news, instead of the style.

When preprocessing the dataset:

original text → LLM → reliable text, unreliable text

When training the model:

original text, reliable text, unreliable text → model

#### Prompt

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

Each time when generating the reliable or unreliable style, we randomly select one of the two adjectives.

#### Example

`reliable.txt` from `fake/gossipcop-13736481`

```text
Kylie Jenner recently revealed her baby, Stormi, to the world after keeping her pregnancy a secret for nine months. As with many celebrities, fans expect Kylie to quickly return to her pre-pregnancy weight through a healthy diet and exercise regimen. However, recent photos suggest that she has lost a significant amount of weight, raising concerns about her health.

There are several theories about Kylie's weight loss secret. One source claims that she follows Kim Kardashian's advice and eats a strict 1,500 calorie-a-day diet, with no carbs or sugar. Another source says that Kylie drinks "detox teas" to help her drop pounds, but it is unclear whether this is effective or safe.

Kylie is also said to be working out with a personal trainer five days a week, which could lead to burnout in the long run. Some sources claim that she is following an extremely calorie-restricted diet, eating as little as 1,000 calories a day and banning junk food around her to avoid temptation.

It is also possible that Kylie is simply losing weight due to good genetics and breastfeeding, as one source tells HollywoodLife.com. However, medical experts advise that women should aim to gain between 25 and 35 pounds during pregnancy and work to lose that weight gradually over six weeks postpartum. Restricting calories, especially for nursing mothers, can affect breast milk quality.

Overall, it is important to approach weight loss after pregnancy in a healthy and sustainable way, rather than relying on extreme diets or quick fixes.
```

`unreliable.txt` from `fake/gossipcop-13736481`

```text
Kylie Jenner has revealed the secret to her dramatic weight loss after giving birth to Stormi, sparking concerns about her health and inspiring envy in her fans.

The Keeping Up with the Kardashians star, who gave birth to her first child with Travis Scott in February, has been shrouded in mystery since giving birth. But recent photos reveal that she has lost an incredible 25 pounds in just two weeks, leaving her fans wondering how she did it.

According to sources, Kylie has been following the advice of her sister Kim Kardashian, who has been giving her private nutrition advice. Kim has reportedly told Kylie to stick to a strict 1,500 calorie-a-day diet and avoid carbs and sugar, even though Kylie is a big fan of In-N-Out fast food.

In addition to Kim's advice, Kylie has also been drinking "detox teas" to help her drop pounds, according to HollywoodLife.com. However, experts warn that these teas don't actually have the ability to "detox" your body and may just cause water weight loss.

Kylie has also been hitting the gym hard to get back into shape, incorporating weight training into her workouts. However, some sources claim that she is working out too much and risking burnout, which can hinder her results in the long run.

Additionally, some sources claim that Kylie is following an extremely calorie-restricted diet, with some even suggesting she is eating as little as 1,000 calories a day. This would be a drastic departure from her usual diet and could be harmful to her health.

Despite these concerns, some sources claim that Kylie's weight loss is simply due to good genetics and breastfeeding. According to one source, "her biggest weight loss secret is breastfeeding and good genetics. She has always had a great metabolism and breastfeeding has kicked it into high gear."

Experts warn that new mothers should not aim to lose weight quickly after giving birth and should focus on healthy nutrition, sleep, and physical activity instead. Restricting calories if you're a nursing mom can also affect breast milk quality.

Overall, Kylie's dramatic weight loss has left her fans both inspired and concerned about her health. Only time will tell if her weight loss is sustainable and if she will be able to maintain it in the long run.
```

### Veracity Attribution

Ideas: use LLM's knowledge to predict the potencial fake reasons of the news, called veracity attributions.

4 fake reasons:

1. Lack of credible sources
2. False or misleading information
3. Biased opinion
4. Inconsistencies with reputable sources

The veracity attributions ard used as pseudo labels for the news.

We predict the veracity attributions for the original news, the reliable text and the unreliable text.

- original text → `veracity_attributions.txt`
- `reliable.txt` → `veracity_attributions_reliable.txt`
- `unreliable.txt` → `veracity_attributions_unreliable.txt

#### Prompt

```
Article: [news article] Question: Which of the following problems does this article have? Lack of credible sources, False or misleading information, Biased opinion, Inconsistencies with reputable sources. If multiple options apply, provide a commaseparated list ordered from most to least related. Answer "No problems" if none of the options apply.
```

#### Example

`veracity_attributions.txt` from `fake/gossipcop-13736481`

```text
False or misleading information
```

`veracity_attributions_reliable.txt` from `fake/gossipcop-13736481`

```text
Lack of credible sources, False or misleading information, Inconsistencies with reputable sources
```

`veracity_attributions_unreliable.txt` from `fake/gossipcop-13736481`

```text
Lack of credible sources, False or misleading information, Inconsistencies with reputable sources
```

# Dataset Example inside this Repository

We also provide an example of the `gossipcop` dataset and the `gossipcop_SheepDog_chatglm_8k` dataset in the
`data_example` folder of this repository. You can preview the files in the folder without downloading the datasets.

**Structure of this repository**:

```
.
├── LICENSE
├── README.md
├── data
└── data_example
    ├── gossipcop_SheepDog_chatglm_8k_example
    │   ├── fake
    │   │   └── gossipcop-13736481
    │   │       ├── news content.json
    │   │       ├── reliable.txt
    │   │       ├── style_attack.txt
    │   │       ├── unreliable.txt
    │   │       ├── veracity_attributions.txt
    │   │       ├── veracity_attributions_reliable.txt
    │   │       └── veracity_attributions_unreliable.txt
    │   └── real
    │       └── gossipcop-841804
    │           ├── news content.json
    │           ├── reliable.txt
    │           ├── style_attack.txt
    │           ├── unreliable.txt
    │           ├── veracity_attributions.txt
    │           ├── veracity_attributions_reliable.txt
    │           └── veracity_attributions_unreliable.txt
    └── gossipcop_example
        ├── fake
        │   └── gossipcop-13736481
        │       └── news content.json
        └── real
            └── gossipcop-841804
                └── news content.json

13 directories, 18 files
```

# Reference

If you use this code, please cite the following paper:

FakeNewsNet: proposed the `gossipcop` dataset.

```
@article{shu2018fakenewsnet,
  title={FakeNewsNet: A Data Repository with News Content, Social Context and Dynamic Information for Studying Fake News on Social Media},
  author={Shu, Kai and  Mahudeswaran, Deepak and Wang, Suhang and Lee, Dongwon and Liu, Huan},
  journal={arXiv preprint arXiv:1809.01286},
  year={2018}
}
```

SheepDog: proposed a method to overcome the style attack to fake news detectors.
Following the method, we produce the `gossipcop_SheepDog_chatglm_8k` dataset.

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

