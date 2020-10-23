KELM Corpus

For details describing the origin of this dataset, please refer to "Large Scale Knowledge Graph Based Synthetic Corpus Generation for Knowledge-Enhanced Language Model Pre-training", Oshin Agarwal, Heming Ge, Siamak Shakeri, Rami Al-Rfou.

This corpus consists of two parts: a training corpus and a generated corpus.

Part 1: Training corpus
The training corpus consists of 3 files:
1. https://storage.googleapis.com/gresearch/kelm-corpus/quadruples-train.tsv
2. https://storage.googleapis.com/gresearch/kelm-corpus/quadruples-validation.tsv
3. https://storage.googleapis.com/gresearch/kelm-corpus/quadruples-test.tsv
These are train, validation, and test sets, respectively. Each file contains "quadruples", i.e. Wikidata triples along with a corresponding Wikipedia sentence. The first column of each tsv file is the Wikidata triple, and the second column is the Wikipedia sentence. Note that the Wikidata triples are of the form "<subject> <relation> <object>" where some relations have sub-relations, e.g. "<subject> <relation> <object1> <sub-relation1> <object2> <sub-relation2> <object3>". For more details please refer to the paper mentioned earlier.

Part 2: Generated corpus
https://storage.googleapis.com/gresearch/kelm-corpus/kelm_generated_corpus.jsonl
This corpus contains ~15M sentences synthetically generated using a T5 model fine-tuned on the data from Part 1. The format is JSON with the generated sentence being in the "candidate" field and the reference Wikidata triple in the "reference" field.
