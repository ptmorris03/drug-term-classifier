# drug-term-classifier

![](https://github.com/ptmorris03/drug-term-classifier/blob/main/drug_terms.png?raw=true)

A Named Entity Recognition (NER) classifier trained to detect novel drug terms based on context. The classifier was trained on ~8,000 hand-labeled drug subreddit comments using a Transformer neural network in the [SpaCy](https://spacy.io/) Python library.

# Install
1. `pip install spacy[transformers]`
2. `wget https://github.com/ptmorris03/drug-term-classifier/releases/download/spacy_weights/drug_detector_weights.zip`
3. `unzip drug_detector_weights.zip`

# Usage
```python3
import spacy

classifier = spacy.load("drug_detector_weights/")

text = """Nice, thanks for the trip report. 
    I'll probably be trying 4-FMA next week. 
    I'm curious to see how it compares to 6-APB.
    I think I might miss the psychedelic edge 6-APB offers, but we'll see."""

output = classifier(text)
drug_terms = output.ents

print(drug_terms)
for drug_term in drug_terms:
    print(str(drug_term), drug_term.start, drug_term.end)
```
```
(4-FMA, 6-APB, 6-APB)
4-FMA 14 17
6-APB 30 33
6-APB 43 46
```
