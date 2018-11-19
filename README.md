# Bioscope-folds
The exact text numbers used for 10-fold cross validation in Scope negation detection papers

You can download the bioscope dataset at  http://rgai.inf.u-szeged.hu/index.php?lang=en&page=bioscope 

Text numbers correspond to ids of the original dataset file xml mark-up.

```
<Document type="Biological_abstract"><DocID type="PMID"> *1984449* </DocID><DocumentPart type="Title">
<sentence id="S1.1">Induction of NF-KB during monocyte differentiation by HIV type 1 infection.</sentence></DocumentPart><DocumentPart type="AbstractText">
<sentence id="S1.2">The production of human immunodeficiency virus type 1 (HIV-1) progeny was followed in the U937 promonocytic cell line after stimulation either with retinoic acid or PMA, and in purified human monocytes and macrophages.</sentence>
<sentence id="S1.3">Electrophoretic mobility shift assays and Southwestern blotting experiments were used to detect the binding of cellular transactivation factor NF-KB to the double repeat-KB enhancer sequence located in the long terminal repeat.</sentence><sentence id="S1.4">PMA treatment, and <xcope id="X1.4.1"><cue type="negation" ref="X1.4.1">not</cue> retinoic acid treatment of the U937 cells</xcope> acts in inducing NF-KB expression in the nuclei.</sentence>
```


*On reproducibility and evaluation:*

1. If you are doing a token-by-token evaluation and are reporting a majority class token based F1, your tokenization matters : the authors of the paper used spacy <link> tokenizer with no additional modifications.

2. Remember that negations can overlap !

* If you have the negation cue information available at train/test time, create a cope for each negation cue present in the sentence and  mark the corresponding  negation span for each cue.  

* If you don't have the  gold cue information at train/test time the system would not be able to tell the difference between a token that is inside of multiple negations spans vs one span.  This mode of evaluation is less sound from the linguistic point of view, but important from a practical point of view (Since it is unlikely that at application time your system will have access to labeled golden negation cues)

