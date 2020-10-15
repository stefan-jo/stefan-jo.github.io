# NLP Summit 2020

[Note: This blog post is work in progress]

I want to kick off this blog by describing my impressions and take-aways from attending the [NLP Summit 2020: Applied Natural Language Processing](https://www.nlpsummit.org/) which took place virtually between October 6th and 9th. [John Snow Labs](https://www.johnsnowlabs.com/), the main creator behind [Spark NLP](https://github.com/JohnSnowLabs/spark-nlp) and organizer of the summit put together a diverse and interesting program for the four conference days.

Overall I really enjoyed the conference. I especially liked the focus on *applied* NLP, presenting many specific NLP use cases from industry as well as topics such as product management, model deployment and data annotation. Working myself at the intersection of applied NLP research, data science and engineering, I recognized many common pain points and lessons learned from my own experience during the conference. Please note that this blog post only describes my own experience and doesn't give a full picture of the conference. Even though I tried to attend as many sessions as possible, I am sure that I still missed some great talks. 

I will divide this blog post into three sections:
1. The state of Applied NLP in 2020
2. The importance of data annotation
3. My personal highlights

## 1. The state of Applied NLP in 2020

The field of applied NLP has made tremendous progress over the last couple of years and continues to grow. Not only are academic benchmarks being beaten at a regular rate, but companies are also increasingly applying these new technologies to their use cases. The field is still very young, with only a minority of companies having NLP models in production for more than five years. However, companies are investing. According to the *2020 NLP Survey Report* by Ben Lorica and Paco Nathan, "53% of respondents who are Technical Leaders stated their NLP budget was at least 10% higher compared to 2019". 

When it comes to specific use cases, document classification, named entity recognition and sentiment analysis are still the most popular NLP tasks. Given the sheer amount of text documents that companies are processing on a daily basis and the recent rate of improvement of NLP techniques, I believe that we will see an enourmous demand for NLP tools, platforms, engineers and researchers in the coming years. Clément Delangue, CEO at huggingface, even went so far as giving a keynote titled "NLP is going to be the most transformational tech of the decade!", basing this claim on the fact that most of our day, both at work and in private, is spent using natural language, which finally can be  accurately processed by machines thanks to recent improvements. 

Just to mention a few of the many exciting use cases that were presented at the conference: 
- automated de-identification of medial records to enable the processing of sensitive documents such as in healthcare
- above-human-level-performance document classification and *abstractive* (!) summarization of documents in the legal domain
- using ML-powered intent recognition, curated templates and knowledge graphs to build effective chatbots

Which tools are used in industry?

Even though from following the Deep Learning community on twitter one might have the impression that everyone uses the huggingface transformers library (disclaimer: I'm a big fan myself) the reality paints a somewhat different picture. According to the above-mentioned survey, the three most-used NLP libraries are Spark NLP, spaCy and Allen NLP, with huggingface landing on rank 7 (which is still very impressive for such a young library). Which tool is the right fit for a given project strongly depends on the specific requirements. Spark NLP and spaCy provide easy-to-use, reliable and efficient libraries for a variety of practical NLP use cases. Allen NLP might be a better suited for researchers. For state-of-the-art pre-trained transformer models one very likely would choose huggingface transformers. For topic modelling gensim is still very popular. For part-of-speech-tagging or dependency parsing Stanford CoreNLP might be the best choice. 

Even though a majority of companies use at least one of the leading NLP cloud services, there are still many challenges to be considered. Among them are price, missing customizability and features, low accuracy, unwillingness to share data and missing support of certain languages. 

Please download and have a look at the [2020 NLP Survey Report](https://gradientflow.com/2020nlpsurvey/) for more details. 

## 2. The importance of data annotation

- Multiple labelers, consensus
- Alignment sessions with team and clients
- Define and review clear annotation guidelines
- Use domain experts for annotation!
- Use annotation tools! Prodigy or in-house
- Aim for high IAA (Inter annotator agreement)

## 3. My personal highlights

- Joel Grus (Principal Engineer @ Capital Group): Proof-of-concept delight
- Christine Gerpheide (CTO @ Bespoke): NLP research to production
- Moshe Wasserblat (NLP & DL Research Manager @ Intel): Efficient DL NLP in production



