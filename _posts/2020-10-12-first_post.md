# NLP Summit 2020

[Note: This blog post is work in progress]

I want to kick off this blog by describing my impressions and take-aways from attending the [NLP Summit 2020: Applied Natural Language Processing](https://www.nlpsummit.org/) which took place virtually between October 6th and 9th. [John Snow Labs](https://www.johnsnowlabs.com/), the main creator behind [Spark NLP](https://github.com/JohnSnowLabs/spark-nlp) and organizer of the summit put together a diverse and interesting program for the four conference days.

Overall I really enjoyed the conference. I especially liked the focus on *applied* NLP, presenting many specific NLP use cases from industry as well as topics such as product management, model deployment and data annotation. Working myself at the intersection of applied NLP research, data science and engineering, I recognized many common pain points and lessons learned from my own experience during the conference. Please note that this blog post only describes my own experience and doesn't give a full picture of the conference. Even though I tried to attend as many sessions as possible, I am sure that I still missed some great talks. 

## 1. The state of Applied NLP in 2020

The field of applied NLP has made tremendous progress over the last couple of years and continues to grow. Not only are academic benchmarks being beaten at a regular rate, but companies are also increasingly applying these new technologies to their use cases. The field is still very young, with only a minority of companies having NLP models in production for more than five years. However, companies are investing. According to the [2020 NLP Survey Report](https://gradientflow.com/2020nlpsurvey/) by Ben Lorica and Paco Nathan, "53% of respondents who are Technical Leaders stated their NLP budget was at least 10% higher compared to 2019". 

When it comes to specific use cases, document classification, named entity recognition and sentiment analysis are still the most popular NLP tasks. Given the sheer amount of text documents that companies are processing on a daily basis and the recent rate of improvement of NLP techniques, I believe that we will see an enourmous demand for NLP tools, platforms, engineers and researchers in the coming years. Clément Delangue, CEO at [huggingface](https://huggingface.co/), even went so far as giving a keynote titled "NLP is going to be the most transformational tech of the decade!", basing this claim on the fact that most of our day, both at work and in private, is spent using natural language, which finally can be  accurately processed by machines thanks to recent improvements. 

Just to mention a few of the many exciting use cases that were presented at the conference: 
- automated de-identification of medial records to enable the processing of sensitive documents such as in healthcare
- above-human-level-performance document classification and *abstractive* (!) summarization of documents in the legal domain
- using ML-powered intent recognition, curated templates and knowledge graphs to build effective chatbots

**Which tools are used in industry?**

Even though from following the Deep Learning community on twitter one might have the impression that everyone uses the huggingface transformers library (disclaimer: I'm a big fan myself) the reality paints a somewhat different picture. According to the above-mentioned survey, the three most-used NLP libraries are [Spark NLP](https://github.com/JohnSnowLabs/spark-nlp), [spaCy](https://spacy.io/) and [Allen NLP](https://allennlp.org/), with huggingface landing on rank 7 (which is still very impressive for such a young library). Which tool is the right fit for a given project strongly depends on the specific requirements. Spark NLP and spaCy provide easy-to-use, reliable and efficient libraries for a variety of practical NLP use cases. Allen NLP might be a better suited for researchers. For state-of-the-art pre-trained transformer models one very likely would choose [huggingface transformers](https://huggingface.co/transformers/). For topic modelling [gensim](https://radimrehurek.com/gensim/) is still very popular. For part-of-speech-tagging or dependency parsing [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/) might be the best choice. A newcomer is the Berlin-based starup [Rasa](https://rasa.com/) that provides an open source framework and a tool called Rasa X for developing contextual AI assistants. 

Even though a majority of companies use at least one of the leading NLP cloud services, there are still many challenges to be considered. Among them are price, missing customizability and features, low accuracy, unwillingness to share data and missing support of certain languages. 

Please download and have a look at the [2020 NLP Survey Report](https://gradientflow.com/2020nlpsurvey/) for more details. 

## 2. On the importance of data annotation

Data annotation or labelling is often considered an uncool, unqualified and strenuous task that *has to be* completed before finally being able to train a fancy model. However, in reality it is one of the most crucial tasks of completing a successful machine learning project that deserves more attention. Without clear guidelines and best practices, data annotation can become very expensive and even lead to the failure of machine learning projects due to insufficient data quality. It was great to see the topic being discussed repeatedly during several session at the NLP Summit 2020. Rebecca Leung and Marianne Mak from John Snow Labs even gave an entire talk about "Lessons learned annotating training data for healthcare NLP projects". Here are some of their insights as well as ideas from other talks and my own experience. 

**Data annotation should be done by experts!** While it may be relatively easy to draw a bounding box around a street sign, most NLP annotation tasks require serious skills. If you want to have a good dataset, annotation needs to be done by qualified domain-experts. For sensitive areas such as healthcare or legal, this might even require having a PhD in the respective field. Moreover, annotation requires incredible focus, speed and endurance. Great annotators should be appreciated and well compensated. 

**Go for quality, not quantity!** Even if you have experts annotating your data, they can still make some mistakes. Some label types (e.g. sentiment) are very subjective and depend on the opinion of a given annotator. Training a machine learning model on smaller, high-quality datasets can lead to better results than training on larger, but noisy and inconsistent data. If the annotation task is subjective or ambiguous, it may help to let two (or more) annotators label the same examples and go by consensus or majority voting.

**Define and review clear annotation guidelines!** It is essential to clearly define guidelines for each annotation project. Formulating guidelines helps current annotators structure their thoughts and future annotators during onboarding. However, these guidelines are not set in stone but can evolve over time. It is important to hold regular (e.g. weekly) review sessions with team members, data scientists and clients to make sure everybody is and stays aligned. 

**Use annotation tools!!!** If there is only one lesson learned about data annotation it is to use specialized tools. It is common best practice to use software tools to significantly speed up the annotation process by providing a clear interface, keyboard shortcuts and workflow support. Moreover, putting the model in the loop and using active learning techniques can make annotators even more efficient. Companies either build their own tools or use commerical ones, such as [Prodigy](https://prodi.gy/) from the makers of spaCy. 

## 3. My personal highlights

In this last section I want to briefly summarize my three personal highlights from the conference. 

Joel Grus, Principal Engineer at Capital Group, gave an insightful and entertaining keynote titled "Proof-of-Concept delight". Drawing on his own experience, Joel demonstrated how to build a PoC in about four hours using modern NLP tools. Here are the main steps he follows: 
1. Identify the business problem: find out what task needs to be solved
2. Find the ML problem: formulate the task as a machine learning problem
3. Find a dataset: either you already have data or you need to find a suitable dataset
4. Scope down relentlessly: simplify the problem until it is the simplest useful version 
5. Create a data model: Joel prefers a typed representation using NamedTuple over pandas for NLP datasets, since those often do not come in a tabular structure but rather have a one-to-many relationship, e.g. one line of text has multiple labels or named entities
6. Explore and clean your data: don't spend ages here but do the necessary cleanup
7. Get labels: either from the dataset or create labels yourself using tools like Prodigy or [Snorkel](https://www.snorkel.ai/)
8. Choose a really simple off-the-shelf model and adapt it just enough to work on your problem
9. Train the model and evaluate on a hold out set using the right metrics
10. Build a demo web app with a text field and get predictions functionality. [Streamlit](https://www.streamlit.io/) makes is extremely easy
11. Take a risk and give the demo to customers. If they like it, build a production version. If not go back and improve the PoC.

Christine Gerpheide, CTO at [Bespoke](https://www.be-spoke.io/index.html), presented two case studies about taking NLP from research to production. After giving a crash course on building chatbots, Christine walked us through the steps Bespoke takes before putting NLP models in production:
1. Identify opportunities for applying machine learning. It's ok to use simple methods at this stage, e.g. pattern matching using regular expression
2. Do research, then build a prototype. Benchmark different approaches, e.g. baseline vs. custom development vs. cloud service
3. Have a go/no go meeting. Decide if there is potential and which approach to follow
4. Build a Minimum Viable Product and test it on a sub-set of users to get real feedback
5. Improve based on feedback, clearn up the code and roll-out to all users

Moshe Wasserblat, NLP & DL Research Manager at the [Intel AI Lab](https://www.intel.com/content/www/us/en/artificial-intelligence/overview.html), gave a talk on the efficient use of deep learning in production. Given the size and computational cost of recent transformer-based language models (think of T5, Turing-NLG and especially GPT-3) it is important to also consider the practicality of implementing these models in production. There are several attempts to make transformer models smaller, such as quantization, pruning, early prediction, weight sharing or distillation. [DistilBERT](https://arxiv.org/abs/1910.01108) from huggingface is 40% smaller and 60% faster than BERT, while maintaining 97% of its language understanding capabilities. Other even smaller yet powerful transformer models are [MobileBERT](https://arxiv.org/abs/2004.02984), [TinyBERT](https://arxiv.org/abs/1909.10351) and [aLBERT](https://arxiv.org/abs/1909.11942), which are easier to fine-tune and deploy. For extreme compression and inference speed up, it is even possible to distil BERT into simpler models like LSTMs, CNNs or CBOW models. Personally I am very excited about the topic of making state-of-the-art NLP models more efficient for practical purposes. There is more to come at the [SustaiNLP](https://sites.google.com/view/sustainlp2020/home) workshop at [EMNLP 2020](https://2020.emnlp.org/). 

Thanks for reading! Please let me know your feedback!



