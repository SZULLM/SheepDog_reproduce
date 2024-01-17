# SheepDog_reproduce

This repository contains the **gossipcop** dataset and its extended dataset **gossipcop_SheepDog_chatglm_8k**.

You can download the datasets
from [Google Drive](https://drive.google.com/file/d/1a1gIVwLb-BvzomRHmFzXzGRLNHvbrEHY/view?usp=drive_link). Then put
them into data folder and unzip them.

# Table of Content

1. [Overview](#overview)
2. [Dataset Structure](#dataset-structure)
3. [Example of the Files](#example-of-the-files)
    1. [fake news](#fake-news)
    2. [real news](#real-news)
4. [LLM-Empowered News Reframing](#llm-empowered-news-reframing)
5. [Reference](#reference)

# Overview

The **gossipcop** dataset is from [FakeNewsNet](https://github.com/KaiDMML/FakeNewsNet?tab=readme-ov-files).
It is a subset of the original dataset, which only contains the news articles.

The **gossipcop_SheepDog_chatglm_8k** dataset is an extended version of the subset of the **gossipcop** dataset,
following the steps from the
paper [Fake News in Sheep's Clothing: Robust Fake News Detection Against LLM-Empowered Style Attacks](https://arxiv.org/abs/2310.10830) (
SheepDog).

**SheepDog** presents the style-related vulnerability of state-of-the-art text-based fake news detectors to
LLM-empowered style attacks.
It also proposes a style-agnostic fake news detector, which is robust against LLM-empowered style attacks.

# Dataset Structure

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

The **gossipcop** dataset contains 2 folders (source): fake and real. It contains 4717 fake news articles and 14991 real
news articles.

Each source folder contains multiple folders (news articles). The folder name is the news article id, such
as `gossipcop-13736481`.

Each article folder contains a file named **news content.json**. It contains the information of the news articles from
the corresponding news source, including url, text, images (if any), etc.

The **gossipcop_SheepDog_chatglm_8k** contains in total 8k news articles, 4k for each source, which are randomly
selected from the **gossipcop** dataset.

Besides the **news content.json** file, each article folder contains 6 extra files: **style_attack.txt**,
**reliable.txt**, **unreliable.txt**, **veracity_attributions.txt**, **veracity_attributions_reliable.txt**,
**veracity_attributions_unreliable.txt**.

The news content.json file contains the original news text. Based on this text, using the LLM model, we generate the
style attack text, reliable text, unreliable text.

We further use LLM model to generate the veracity attributions for the news articles.

The veracity_attributions.txt file contains the veracity attributions for the original news articles. The
veracity_attributions_reliable.txt and veracity_attributions_unreliable.txt files contain the veracity attributions for
the reliable and unreliable text, respectively.

We utilize the [ChatGLM3](https://github.com/THUDM/ChatGLM3) model to reframe the news articles and predict the veracity
attributions. More details can be found in below section [LLM-Empowered News Reframing](#llm-empowered-news-reframing).

# Example of the Files

## fake news

### news contents.json

`gossipcop_example/fake/gossipcop-13736481/news content.json`

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

### style_attack.txt

```text
Kylie Jenner has finally revealed the arrival of her baby, Stormi, to the world after keeping her pregnancy under wraps for nine months. While many expected the reality star to quickly bounce back into shape with a healthy diet and exercise regimen, recent photos suggest that she has lost a significant amount of weight, leaving fans to wonder if it's healthy.

So, what's Kylie's secret to losing 25 pounds in just two weeks? According to various sources, the Keeping Up with the Kardashians star is following in the footsteps of her sister, Kim Kardashian, and is eating a super-strict diet that involves eating only 1,500 calories per day and avoiding carbs and sugar, even though she has a reported addiction to In-N-Out fast food.

In addition to her diet, Kylie is also said to be drinking "detox teas" to help her drop pounds. However, experts warn that teas do not actually have the ability to "detox" the body and that drinking them will not necessarily help you lose weight.

Kylie is also said to be incorporating weight training into her workout routine, which is a good way to burn calories and build muscle. However, working out too much can lead to burnout, which can hinder weight loss results in the long run.

There are also rumors that Kylie is sticking to an extremely calorie-restricted diet, with some sources claiming that she is eating as little as 1,000 calories per day. However, experts suggest that this is not a healthy approach to weight loss and that new mothers should focus on a healthy diet instead of cutting calories.

Finally, some sources suggest that Kylie's weight loss may be due to good genetics and breastfeeding, rather than extreme dieting. While it is possible that Kylie is not going to any extremes after all, it is important for new mothers to focus on good nutrition, sleep, and physical activity to keep energy levels up and maintain a healthy weight.
```

### reliable.txt

```text
Kylie Jenner recently revealed her baby, Stormi, to the world after keeping her pregnancy a secret for nine months. As with many celebrities, fans expect Kylie to quickly return to her pre-pregnancy weight through a healthy diet and exercise regimen. However, recent photos suggest that she has lost a significant amount of weight, raising concerns about her health.

There are several theories about Kylie's weight loss secret. One source claims that she follows Kim Kardashian's advice and eats a strict 1,500 calorie-a-day diet, with no carbs or sugar. Another source says that Kylie drinks "detox teas" to help her drop pounds, but it is unclear whether this is effective or safe.

Kylie is also said to be working out with a personal trainer five days a week, which could lead to burnout in the long run. Some sources claim that she is following an extremely calorie-restricted diet, eating as little as 1,000 calories a day and banning junk food around her to avoid temptation.

It is also possible that Kylie is simply losing weight due to good genetics and breastfeeding, as one source tells HollywoodLife.com. However, medical experts advise that women should aim to gain between 25 and 35 pounds during pregnancy and work to lose that weight gradually over six weeks postpartum. Restricting calories, especially for nursing mothers, can affect breast milk quality.

Overall, it is important to approach weight loss after pregnancy in a healthy and sustainable way, rather than relying on extreme diets or quick fixes.
```

### unreliable.txt

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

### veracity_attributions.txt

```text
False or misleading information
```

### veracity_attributions_reliable.txt

```text
Lack of credible sources, False or misleading information, Inconsistencies with reputable sources
```

### veracity_attributions_unreliable.txt

```text
Lack of credible sources, False or misleading information, Inconsistencies with reputable sources
```

## real news

### news contents.json

```json
{
  "url": "https://www.cosmopolitan.com/uk/entertainment/a9244918/listen-to-harry-styles-sign-of-the-times/",
  "text": "YOU GUYS, Harry Styles from One Direction just played his debut solo single 'Sign Of The Times' on BBC Radio 1 during a 2-hour interview with Nick Grimshaw - AND IT'S SO GOOD.\n\nSince One Direction went on hiatus last summer, Harry Styles has been a busy little bee - after landing a role in Christopher Nolan's Dunkirk and going to Jamaica to record his debut solo album.\n\nToday, he released the first single 'Sign Of The Times'. So, you wanna hear it? HERE IT IS:\n\nYeah, we're obsessed.\n\nHarry also spoke to Nick for two hours (TWO HOURS) about everything from what Adele gave him for his birthday to his 'weird' and 'wrong' approach to dating.\n\nOn the topic of his forthcoming album, Harry said he was nervous about the reaction it would receive, but also incredibly proud of it. He commented:\n\n\"It’s a bit weird, I feel like I’ve been hibernating for so long now and you hear it in the safety of the studio and now it’s time to give birth … it’s the song (debut single) I’m most proud of writing.\n\n\"In the least weird way possible, it’s my favourite album to listen to at the moment… I think if you put out something that you don’t stand behind and really love…then if it doesn’t go well then you could regret not doing what you wanted to do. Whereas if nothing happens with it, I love it you know so I think that’s what you should do.\"\n\nBear Grylls // Digital Spy\n\nOn what inspired the album, Harry added:\n\n“I think a lot of people, especially at labels separate it because they work in music that it’s a broader understanding of music than people who are listening… I think we are all fans of music and I think we made it as the fan… I hope we did a good job but I really like the album so I hope people like it.”\n\nYou go, Glen Coco.",
  "images": [
    "https://www.cosmopolitan.com/_assets/design-tokens/cosmopolitan/static/images/logos/logo.3c052be.svg?primary=%2523ffffff",
    "https://hips.hearstapps.com/hmg-prod/images/screenshot-2023-12-24-at-11-53-29-65881bc3975b7.png?crop=1.00xw:0.891xh;0,0&resize=360:*",
    "https://hips.hearstapps.com/hmg-prod/images/leighton-meester-exmas-6586adc4a5178.jpg?crop=1.00xw:0.670xh;0,0&resize=360:*",
    "https://hips.hearstapps.com/hmg-prod/images/gladiators-658c0570e6039.jpeg?crop=0.710xw:1.00xh;0.146xw,0&resize=360:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/search.f1c199c.svg",
    "https://hips.hearstapps.com/hmg-prod/images/travis-kourtney-love-note-1640255410.png?crop=0.801xw:0.641xh;0.0737xw,0.0167xh&resize=360:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/en-gb/static/images/logos/network-logo.eae65ae.svg?primary=%2523ffffff",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/play.db7c035.svg?primary=%2523ffffff",
    "https://hips.hearstapps.com/hmg-prod/images/bridgerton-302-unit-02420r-658bfcb46fee3.jpeg?crop=0.668xw:1.00xh;0.201xw,0&resize=360:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/social/instagram.f282b14.svg?primary=%2523DA8EEA&id=social-button-icon",
    "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1.00xw:0.502xh;0,0.224xh&resize=1200:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/social/x.3361b6d.svg?primary=%2523DA8EEA&id=social-button-icon",
    "https://hips.hearstapps.com/vidthumb/images/stt-amber-gill-yt-1641312470.jpg?crop=1xw:1xh;center,top&resize=1200:*",
    "https://hips.hearstapps.com/rover/profile_photos/0705f70f-1709-4777-afb2-62e0e0441313.jpg?fill=1:1&resize=160:*",
    "https://hips.hearstapps.com/hmg-prod/images/mean-girls-1612442204.jpeg?crop=0.665xw:1.00xh;0.210xw,0&resize=360:*",
    "https://hips.hearstapps.com/hmg-prod/images/kim-kardashian-bikini-640992816b1b9.png?crop=1.00xw:0.841xh;0,0.00134xh&resize=360:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/social/pinterest.e8cf655.svg?primary=%2523DA8EEA&id=social-button-icon",
    "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1.00xw:0.564xh;0,0.203xh&resize=768:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/social/youtube.ce3e1ae.svg?primary=%2523DA8EEA&id=social-button-icon",
    "https://hips.hearstapps.com/hmg-prod/images/kylie-and-timothe-e-654376f65a72c.jpg?crop=0.505xw:1.00xh;0.176xw,0&resize=360:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/social/facebook.a5a3a69.svg?primary=%2523DA8EEA&id=social-button-icon",
    "https://hips.hearstapps.com/hmg-prod/images/hen-party-houses-77-1595424238.jpg?crop=0.503xw:1.00xh;0.311xw,0&resize=360:*",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/icons/social/pinterest.e8cf655.svg?primary=%2523ffffff",
    "https://www.cosmopolitan.com/_assets/design-tokens/fre/static/images/logos/ipso-regulated.9922b5a.svg?primary=white",
    "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?resize=980:*",
    "https://hips.hearstapps.com/hmg-prod/images/dominicwest-65883c634bf99.jpg?crop=1.00xw:0.668xh;0,0&resize=360:*",
    "https://hips.hearstapps.com/hmg-prod/images/xx-ways-love-actually-would-be-different-in-2023-657b359502a51.jpg?crop=0.506xw:1.00xh;0.248xw,0&resize=360:*",
    "https://hips.hearstapps.com/hmg-prod/images/saltburn-nude-scene-655b39fcd865e.jpg?crop=0.5023255813953489xw:1xh;center,top&resize=360:*"
  ],
  "top_img": "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1.00xw:0.502xh;0,0.224xh&resize=1200:*",
  "keywords": [],
  "authors": [],
  "canonical_link": "https://www.cosmopolitan.com/uk/entertainment/a9244918/listen-to-harry-styles-sign-of-the-times/",
  "title": "Listen to Harry Styles' first solo single 'Sign Of The Times'",
  "meta_data": {
    "viewport": "width=device-width, initial-scale=1.0",
    "X-UA-Compatible": "IE=edge,chrom=1",
    "msapplication-tap-highlight": "no",
    "title": "Listen to Harry Styles' first solo single 'Sign Of The Times'",
    "description": "One Direction's Harry Styles played his debut solo song 'Sign Of The Times' on Nick Grimshaw's BBC Radio 1 show - and it's SO GOOD.",
    "keywords": "Harry Styles, One Direction, Sign Of The Times, Listen, Single, song, solo song, debut solo song, stream online, harry styles leaked, track, listen",
    "og": {
      "type": "article",
      "site_name": "Cosmopolitan",
      "title": "Listen to Harry Styles' first solo single 'Sign Of The Times'",
      "description": "IT'S SO GOOD YOU'RE GONNA LOVE IT",
      "image": {
        "identifier": "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1.00xw:0.502xh;0,0.224xh&resize=1200:*",
        "width": 1200,
        "height": 600
      },
      "url": "https://www.cosmopolitan.com/uk/entertainment/a9244918/listen-to-harry-styles-sign-of-the-times/"
    },
    "theme-color": "#000000",
    "fb": {
      "app_id": 211620818858710
    },
    "article": {
      "publisher": "https://facebook.com/cosmopolitanuk",
      "section": "Entertainment",
      "modified_time": "2022-07-29T11:47:49Z",
      "published_time": "2017-04-07T07:11:00Z"
    },
    "twitter": {
      "site": "@CosmopolitanUK",
      "image": "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1.00xw:0.502xh;0,0.224xh&resize=640:*",
      "card": "summary_large_image"
    },
    "google-site-verification": "9QqScyr6oRc1iBU6yEjb9Ww8aQvv8v-cCm0TKu2J2iw",
    "robots": "max-image-preview:large,max-snippet:-1,max-video-preview:30",
    "thumbnail": "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1xw:1xh;center,top&resize=320:*",
    "sailthru.image.full": "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1.00xw:0.502xh;0,0.224xh&resize=320:*",
    "sailthru.image.thumb": "https://hips.hearstapps.com/hmg-prod/images/legacy-fre-image-placeholder-1655513735.png?crop=1xw:1xh;center,top",
    "auto-publish": "timely",
    "sailthru.excerpt": "YOU GUYS, Harry Styles from One Direction just played his debut solo single 'Sign Of The Times' on BBC Radio 1 during a 2-hour interview with Nick Grimshaw - AND IT'S SO GOOD.\n\nSince One Direction went on hiatus last summer, Harry Styles has been a busy little bee - after",
    "sailthru.tags": "entertainment,Entertainment",
    "sailthru.date": "2017-04-07 07:11:00",
    "sailthru.socialtitle": "Listen to Harry Styles' first solo single 'Sign Of The Times'",
    "sailthru.contenttype": "standard-article",
    "m1": ".content-hed",
    "m2": ".content-dek p",
    "next-head-count": 46
  },
  "movies": [],
  "publish_date": 1.49154906E9,
  "source": "https://www.cosmopolitan.com",
  "summary": ""
}
```

### style_attack.txt

```text
"BREAKING NEWS: Harry Styles Makes Solo Debut with Blistering New Single 'Sign Of The Times!'

After months of teasing, One Direction heartthrob Harry Styles has finally unleashed his highly anticipated debut solo single 'Sign Of The Times'. And let me tell you, it's everything we've been waiting for!

Since the band went on hiatus last summer, Harry has been busy filming Christopher Nolan's Dunkirk and recording his solo album in Jamaica. And today, he made his solo debut with an electrifying performance of 'Sign Of The Times' on BBC Radio 1 during a two-hour interview with Nick Grimshaw.

We're obsessed with the song! It's got a beat that's out of this world, and Harry's vocals are as smooth as butter. We can't get enough of it!

But that's not all - Harry also spoke to Nick for two whole hours about everything from what Adele gave him for his birthday to his 'weird' and 'wrong' approach to dating.

On the topic of his forthcoming album, Harry revealed that he was nervous about the reaction it would receive, but also incredibly proud of it. He said:

"It’s a bit weird, I feel like I’ve been hibernating for so long now and you hear it in the safety of the studio and now it’s time to give birth ... it’s the song (debut single) I’m most proud of writing.

"In the least weird way possible, it’s my favourite album to listen to at the moment ... I think if you put out something that you don’t stand behind and really love ... then if it doesn’t go well then you could regret not doing what you wanted to do. Whereas if nothing happens with it, I love it you know so I think that’s what you should do."

So what do you think of Harry's solo debut? Let us know in the comments below! And don't forget to follow us for all the latest Harry Styles news!"```
```

### reliable.txt

```text
Harry Styles, previously a member of the boy band One Direction, has released his debut solo single, "Sign Of The Times." The song premiered during a two-hour interview with Nick Grimshaw on BBC Radio 1 and has been met with widespread appreciation.

Since the hiatus of One Direction last summer, Styles has been actively engaged in his solo career. He landed a role in Christopher Nolan's war film Dunkirk and traveled to Jamaica to record his debut album.

During his interview with Grimshaw, Styles discussed a range of topics, including what Adele gave him for his birthday and his unconventional approach to dating. He also spoke about his upcoming album, expressing nervousness about the reception it might receive but also pride in the work.

When discussing the album's inspiration, Styles noted that he and his collaborators aimed to create music that would appeal to a broad audience, rather than just music industry insiders. He hopes that fans will enjoy the album and that it will be well-received.

Overall, Styles has been a busy bee since One Direction's hiatus, and his debut single and upcoming album show that he is poised for continued success in the music industry.
```

### unreliable.txt

```text
Oh my goodness, have you heard the new solo single from Harry Styles? He just played it on BBC Radio 1 during a 2-hour interview with Nick Grimshaw and it's absolutely amazing. Since One Direction went on hiatus last summer, Harry has been working tirelessly on his debut album and it seems like it's all been worth it.

The first single, 'Sign Of The Times', is perfection. It's been on repeat all day and we can't get enough of it. Harry also spoke to Nick for two hours about everything from what Adele gave him for his birthday to his 'weird' and 'wrong' approach to dating.

On the topic of his forthcoming album, Harry said he was nervous about the reaction it would receive, but also incredibly proud of it. He explained that he's been hibernating for so long now and it's finally time to give birth, and that he's most proud of the song he's releasing as the debut single.

Harry also said that he hopes people will love the album as much as he does, and that if nothing happens with it, he loves it anyway. That's the kind of confidence we love to see in a artist.

We're so excited to hear more from Harry and can't wait to see what the future holds for him. He truly is a star and we are all rooting for him.```
```

### veracity attributions for real news

Note that, the paper **SheepDog** manually set the veracity attributions for real news as `No problems`. Because the
real news is not supposed to have any problems.

So you should ignore the 3 veracity attributions files for real news.

# LLM-Empowered News Reframing

Contains 3 types of news reframing tasks: style attack, style reframing, and veracity attribution.

## Style Attack

```
Rewrite the following article using the style of [publisher name]: [news article]
```

Two selections for the publisher name:

1. National Enquirer
2. The New York Times

National Enquirer is a tabloid, which is used to camouflage real news. The New York Times is a reliable news source,
which is used to camouflage fake news.

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

Each time when generating the reliable or unreliable style, we randomly select one of the two adjectives.

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