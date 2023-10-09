---
license: cc-by-sa-4.0
task_categories:
- multiple-choice
- question-answering
language:
- ja
---

# Dataset Card for JAQKET

This dataset loading script is developed on [GitHub](https://github.com/kumapo/JAQKET-dataset).
Please feel free to open an [issue](https://github.com/kumapo/JAQKET-dataset/issues) or [pull request](https://github.com/kumapo/JAQKET-dataset/pulls).


## Dataset Description

- **Homepage:** https://sites.google.com/view/project-aio/dataset
- **Repository:** https://github.com/kumapo/JAQKET-dataset

### Dataset Summary

From [the original paper](https://www.anlp.jp/proceedings/annual_meeting/2020/pdf_dir/P2-24.pdf):

> 本研究では，日本における質問応答/機械読解研究の促進を目的として，研究者が容易に利用可能な日本語のオープンドメイン QA タスクのデータセット「JAQKET」1を構築する.
> 作成するデータセットは，既存研究 [7] に倣い，Wikipedia2 の記事名を答えとした，日本語のオープンドメイン QA タスクのデータセットである.

### Supported Tasks

#### JAQKET v1.0

From [the original paper](https://www.anlp.jp/proceedings/annual_meeting/2020/pdf_dir/P2-24.pdf):

> 本研究で扱う日本語オープンドメイン QA タスクを定義する.本研究では，クイズの問題文に対して複数(数個から数十個程度)の解答の選択肢が与られ，その選択肢から正解を一つ選択するという択一問題を取り扱う.

#### JAQKET v2.0

From [the homepage](https://sites.google.com/view/project-aio/competition2):

 > 問題として与えられるのはクイズの問題文のみです．その問題文から解答となる文字列を解答として返すシステムを構築してもらいます．

### Languages

The language data in JAQKET is in Japanese.

## Dataset Structure

### Data Instances

When loading a specific configuration, users has to append a version dependent suffix:

#### JAQKET v1.0

```python
from datasets import load_dataset

dataset = load_dataset("kumapo/JAQKET", name="v1.0")

print(dataset)

# DatasetDict({
#     train: Dataset({
#         features: ['qid', 'question', 'answer_entity', 'label', 'answer_candidates', 'contexts'],
#         num_rows: 13061
#     })
#     validation: Dataset({
#         features: ['qid', 'question', 'answer_entity', 'label', 'answer_candidates', 'contexts'],
#         num_rows: 271
#     })
# })
```

An example of the JAQKET v1.0 dataset looks as follows:

```json
{
  "qid": "QA20QBIK-0002",
  "question": "童謡『たなばたさま』の歌詞で、「さらさら」と歌われる植物は何の葉?",
  "answer_entity": "ササ",
  "answer_candidates": [
    "ササ",
    "チシマザサ",
    "クマザサ",
    "アダン",
    "チガヤ",
    "アセビ",
    "ススキ",
    "ホオノキ",
    "マテバシイ",
    "ヤマフジ",
    "ウツギ",
    "タムシバ",
    "ミズキ",
    "アキタブキ",
    "トベラ",
    "クヌギ",
    "ネズミモチ",
    "ヒシ",
    "コブシ",
    "オオウバユリ"
  ],
  "qtype": "なに〜"
}
```

```json
{
  "qid": "QA20QBIK-0026",
  "question": "北海道の中心に位置することから「北海道のへそ」と名乗る、ラベンダーで有名な都市はどこ?",
  "answer_entity": "富良野市",
  "answer_candidates": [
    "富良野市",
    "滝川市",
    "北見市",
    "芦別市",
    "中富良野町",
    "名寄市",
    "網走市",
    "美瑛町",
    "南富良野町",
    "岩見沢市",
    "美唄市",
    "上富良野町",
    "倶知安町",
    "小樽市",
    "歌志内市",
    "旭川市",
    "ニセコ町",
    "北斗市",
    "稚内市",
    "帯広市"
  ],
  "qtype": "どこ"
}
```

#### JAQKET v2.0

```python
from datasets import load_dataset

dataset = load_dataset("kumapo/JAQKET", name="v2.0")

print(dataset)
# DatasetDict({
#     train: Dataset({
#         features: ['qid', 'question', 'answers', 'ctxs'],
#         num_rows: 2154
#     })
#     validation: Dataset({
#         features: ['qid', 'question', 'answers', 'ctxs'],
#         num_rows: 1164
#     })
# })
```

An example of the JAQKET v2.0 dataset looks as follows:

```json
{
   "qid": "QA20QBIK-0002",
   "competition": "第1回AI王",
   "timestamp": "2020/01/27",
   "section": "開発データ問題 (dev1)",
   "number": "2",
   "original_question": "童謡『たなばたさま』の歌詞で、「さらさら」と歌われる植物は何の葉？",
   "original_answer": "ササ",
   "original_additional_info": "",
   "question": "童謡『たなばたさま』の歌詞で、「さらさら」と歌われる植物は何の葉?",
   "answers" :["ササ"]
}
```

## Additional Information

### Citation Information

```bibtex
@InProceedings{Kurihara_nlp2020,
  author =  "鈴木正敏 and 鈴木潤 and 松田耕史 and ⻄田京介 and 井之上直也",
  title =   "JAQKET: クイズを題材にした日本語 QA データセットの構築",
  booktitle =   "言語処理学会第26回年次大会",
  year =    "2020",
  url = "https://www.anlp.jp/proceedings/annual_meeting/2020/pdf_dir/P2-24.pdf"
  note= "in Japanese"}
```
