For details describing the origin of this dataset, please refer to "<a href="https://www.aclweb.org/anthology/2021.naacl-main.278/">Knowledge Graph Based Synthetic Corpus Generation for Knowledge-Enhanced Language Model Pre-training</a>", Oshin Agarwal, Heming Ge, Siamak Shakeri, Rami Al-Rfou.

This corpus consists of two parts: TEKGEN (**Te**xt From **KG Gen**eratiom) training corpus and the generated synthetic KELM (**K**nowledge **E**nhanced **L**anguage **M**odel Pre-training) corpus.

## Part 1: TEKGEN Training Corpus

This is the Wikipedia text--Wikidata KG aligned corpus used to train the data-to-text generation model. Please note that this is a corpus generated with distant supervision and should not be used as gold standard for evaluation.

It consists of 3 files:
1. https://storage.googleapis.com/gresearch/kelm-corpus/updated-2021/quadruples-train.tsv
2. https://storage.googleapis.com/gresearch/kelm-corpus/updated-2021/quadruples-validation.tsv
3. https://storage.googleapis.com/gresearch/kelm-corpus/updated-2021/quadruples-test.tsv

Each file contains one example per line. Each example is a json object with three fields:
1. triples: A list of triples of the form (subject, relation, object). eg. (Person X, award received, Award Y). If the triple has a subproperty, then it is quadruple instead. eg. (Person X, Award Y, received on, Date Z).

2. serialized triples: triples concatenated together as used for input to T5. The format is "&lt;subject&gt; &lt;relation&gt; &lt;object&gt;" where some subjects have multiple relations, e.g. "&lt;subject&gt; &lt;relation1&gt; &lt;object1&gt; &lt;relation2&gt; &lt;object2&gt; &lt;relation3&gt; &lt;object3&gt;". For more details on how these relations are grouped, please refer to the paper.

3. sentence: The wikipedia sentence aligned to these triples.

The names, aliases and Wikidata Ids of the entities can be found in https://storage.googleapis.com/gresearch/kelm-corpus/updated-2021/entities.jsonl.

## Part 2: KELM Corpus

This is a synthetic corpus that consists of the entire Wikidata KG as natural text sentences. It has ~15M sentences synthetically generated using a T5 model fine-tuned on the data from Part 1 with some additional components. It can be used as additional data in language model pre-training as a means to integrate KGs with natural text.

https://storage.googleapis.com/gresearch/kelm-corpus/updated-2021/kelm_generated_corpus.jsonl

Each line is an example as a json object with three fields:

1. triples: A list of triples of the form (subject, relation, object). eg. (Person X, award received, Award Y). If the triple has a subproperty, then it is quadruple instead. eg. (Person X, Award Y, received on, Date Z). These triples are entity subgraphs as described in the paper.

2. serialized triples: triples concatenated together as used for input to T5. The format is "&lt;subject&gt; &lt;relation&gt; &lt;object&gt;" where some subjects have multiple relations, e.g. "&lt;subject&gt; &lt;relation1&gt; &lt;object1&gt; &lt;relation2&gt; &lt;object2&gt; &lt;relation3&gt; &lt;object3&gt;". For more details on how these relations are grouped, please refer to the paper.

3. gen_sentence: The generated natural language sentence for the triples.

About 0.1% of the examples in kelm_generated_corpus.jsonl are missing the "triples" field.

The names, aliases and Wikidata Ids of the entities can be found in https://storage.googleapis.com/gresearch/kelm-corpus/updated-2021/entities.jsonl.


### License

This dataset has been released under the [CC BY-SA 2.0 license](https://creativecommons.org/licenses/by-sa/2.0/).
