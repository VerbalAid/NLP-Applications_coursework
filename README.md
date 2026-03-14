# NLP Applications 1 — Lab Portfolio

Coursework notebooks from the **NLP Applications I** module at **UPV/EHU** (University of the Basque Country), part of the MSc in Language Analysis and Processing. The module covers a progressive stack from basic NLP tooling through to fine-tuning large language models for sequence labelling, argument mining, and natural language generation.

---

## 📚 Module Overview

The labs move through three main toolkits and paradigms:

| Phase | Toolkit | Topic |
|---|---|---|
| 1–2 | spaCy | Linguistic annotation and text classification |
| 3–5 | Flair | Contextual embeddings, NER, and lemmatisation |
| 6–8 | 🤗 Transformers / BERT | Multilabel classification, argument mining, and generation |

---

## 🗂️ Lab Notebooks

### Lab 1 — spaCy Basics
**File:** `spacy_basics_TODO_2_.ipynb`

Introduction to the [spaCy](https://spacy.io) NLP pipeline. Covers loading multilingual language models, tokenisation, POS tagging, morphological analysis, named entity recognition (NER), and sentence segmentation. Includes hands-on comparison of different model sizes and language modules.

**Key concepts:** `nlp` pipeline, `Doc`/`Token`/`Span` objects, entity types, stopword filtering, POS filtering.

**References:**
- [spaCy 101](https://spacy.io/usage/spacy-101)
- [spaCy usage & installation](https://spacy.io/usage)

---

### Lab 2 — Text Classification with spaCy
**File:** `02_train_text_classifier_spacy_2_.ipynb`

Training text classifiers using spaCy on two fake news datasets: a general multi-domain corpus (5 topics) and a celebrity-focused subset. Experiments with multiple architectures including Bag-of-Words (BOW), CNN, and Ensemble models. Inline documentation added throughout as part of the assignment.

**Key concepts:** `textcat` component, BOW vs. CNN vs. Ensemble classifiers, training loop, evaluation metrics.

---

### Lab 3 — Flair Basics & Word Representations
**File:** `03_flair_basics_TODO_5__1_.ipynb`

Introduction to the [Flair](https://flairnlp.github.io/flair/) NLP library. Explores static word embeddings (GloVe, fastText) and Flair's character-based contextual embeddings. Investigates the key difference between context-independent and contextual representations — notably, why the same token (e.g. *Washington*) gets different vectors depending on surrounding context in Flair but not in GloVe.

**Key concepts:** `Sentence`, `WordEmbeddings`, `FlairEmbeddings`, `StackedEmbeddings`, vector comparison with cosine similarity.

**References:**
- [Flair documentation](https://flairnlp.github.io/flair/)
- [Flair embedding tutorials](https://flairnlp.github.io/flair/v0.13.1/tutorial/tutorial-embeddings/index.html)

---

### Lab 4 — NER Training and Tagging with Flair
**File:** `Copy_of_04_flair_ner_training_tagging_TODO_1__1_.ipynb`

Training a Named Entity Recognition model from scratch using Flair's `SequenceTagger` on a language of choice (Basque, using `WordEmbeddings('eu')`). The trained model is then applied to tag a new document, following the IOB2 annotation format.

**Key concepts:** `ColumnCorpus`, `SequenceTagger`, `ModelTrainer`, IOB2 tagging, `WordEmbeddings`, inference on unseen text.

**References:**
- [Flair NER training tutorial](https://flairnlp.github.io/flair/v0.13.1/tutorial/tutorial-training/how-to-train-sequence-tagger.html)
- CoNLL-2003 NER dataset

---

### Lab 5 — Neural Lemmatisation with Flair *(Bonus)*
**File:** `05_train_flair_lemma_TODO_BONUS_3__1_.ipynb`

Extends the NER training pipeline to the task of contextual lemmatisation, using the SIGMORPHON 2019 shared task data. The model predicts edit rules (lemma rules) rather than raw lemma strings, which are then decoded via Levenshtein-based string transformations. Experiments with Classic, Character, and Flair embeddings to compare accuracy.

**Key concepts:** `ColumnCorpus`, lemma rule prediction, `SequenceTagger` for morphology, Levenshtein distance, embedding ablation.

**References:**
- [SIGMORPHON 2019 Shared Task](https://arxiv.org/abs/2109.07958)
- [Flair character embeddings](https://flairnlp.github.io/flair/v0.13.1/tutorial/tutorial-embeddings/flair-embeddings.html)

---

### Lab 6 — Multilabel Aspect Category Detection with BERT *(In Progress)*
**File:** `06_BERT_multilabel_acd_TODO.ipynb`

Fine-tuning `bert-base-uncased` for multilabel Aspect Category Detection (ACD) — a subtask of Aspect-Based Sentiment Analysis (ABSA). The model is trained to simultaneously predict multiple aspect categories per review sentence. Includes investigation of the effect of `max_length` (64, 100, 128) on performance, with F1 micro and accuracy evaluation via scikit-learn.

**Key concepts:** `BertForSequenceClassification`, multilabel one-hot encoding, `BertTokenizer`, `max_length` ablation, classification report.

**References:**
- [HuggingFace Transformers Course — Tokenizers](https://huggingface.co/learn/llm-course/chapter1/1)
- Sentiment Analysis & Opinion Mining lecture slides — Rodrigo Agerri, IXA/ILTAPP ([course page](http://www.ixa.eus/iltapp/))

---

### Lab 7 — Argument Mining with Transformers *(In Progress)*
**File:** `07_Transformers_Argument_Mining_TODO.ipynb`

Fine-tuning a token classification (sequence labelling) model using 🤗 Transformers for Argument Mining — specifically detecting argument components (claims and premises) in the **ABSTRCT** corpus of clinical trial abstracts. Includes adapting a custom dataset loading script (modelled on the CoNLL-2003 script) and performing error analysis on model predictions.

**Key concepts:** `AutoModelForTokenClassification`, `DataCollatorForTokenClassification`, Argument Mining, BIO tagging, cross-lingual transfer, error analysis.

**References:**
- [HuggingFace Datasets](https://github.com/huggingface/datasets)
- Sviridova et al. (2024) — **CasiMedicos-Arg: A Medical Question Answering Dataset Annotated with Explanatory Argumentative Structures** — *EMNLP 2024* — [PDF](https://aclanthology.org/2024.emnlp-main.1026.pdf)
- NLG and Evaluation of LLMs lecture slides — Rodrigo Agerri, IXA/ILTAPP ([course page](http://www.ixa.eus/iltapp/))

---

### Lab 8 — Argument Generation / Counternarrative Generation *(Bonus, In Progress)*
**File:** `08_Transformers_Argument_Generation_BONUS_TODO.ipynb`

Fine-tuning a sequence-to-sequence model for counternarrative generation using the **CONAN** dataset, available in English, Spanish, and Basque. The task involves generating counter-arguments to hateful or harmful statements, evaluated using standard NLG metrics.

**Key concepts:** Seq2seq generation, `AutoModelForSeq2SeqLM`, CONAN dataset, multilingual generation (EN/ES/EU), BLEU/ROUGE evaluation.

**References:**
- [CONAN Dataset](https://github.com/marcoguerini/CONAN#CONAN)
- NLG and Evaluation of LLMs lecture slides — Rodrigo Agerri, IXA/ILTAPP ([course page](http://www.ixa.eus/iltapp/))

---

## 📄 Course Materials & Papers

| Resource | Link |
|---|---|
| spaCy documentation | https://spacy.io/usage/spacy-101 |
| Flair documentation | https://flairnlp.github.io/flair/ |
| HuggingFace LLM Course | https://huggingface.co/learn/llm-course/chapter1/1 |
| SIGMORPHON 2019 (lemmatisation) | https://arxiv.org/abs/2109.07958 |
| CasiMedicos-Arg — EMNLP 2024 | https://aclanthology.org/2024.emnlp-main.1026.pdf |
| CONAN (counternarrative generation) | https://github.com/marcoguerini/CONAN |
| IXA/ILTAPP course page | http://www.ixa.eus/iltapp/ |

---

## 🛠️ Setup

All notebooks were developed in **Google Colab** (GPU runtime). Key dependencies:

```bash
pip install spacy flair transformers datasets scikit-learn pandas torch
```

Individual notebooks include their own installation cells for model-specific packages.

---

## 🏫 Module Info

**Module:** NLP Applications I  
**Programme:** MSc in Language Analysis and Processing  
**Institution:** UPV/EHU — University of the Basque Country  
**Instructor:** Rodrigo Agerri ([IXA Group](http://www.ixa.eus))
