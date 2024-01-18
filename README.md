[![CC BY 4.0][cc-by-shield]][cc-by] [![DOI](https://zenodo.org/badge/351362868.svg)](https://zenodo.org/badge/latestdoi/351362868)


![characters badge](badges/characters.svg) ![regions badge](badges/regions.svg) ![lines badge](badges/lines.svg) ![files badge](badges/files.svg) 

# DAHN Corpus
## Description
Ground Truth dataset for French 20th typewritten OCR

## Content
**ALTO/PAGE XML files from the same corpus, divided into 5 sub-corpus**

| # | name | nb of images | GT for segmenter? | GT for recognizer? | description |
| --- | :---- | :---: | :---: | :---: | :---: |
| 0 | batch-00 | (48) | y | n | Manual segmentation on pages with straight and regular lines |
| 1 | batch-01 | (258) | y | y | Long letters, many lines per page, mostly straight lines but also narrow tight lines. Several pages contain lists, tables and many capital letters words. |
| 2 | batch-02 | (59) | y | y | Long letters, many lines per page, mostly straigt lines but also narrow tight lines. Approximatively ten letters with handwritten texts. |
| 3 | batch-03 | (84) | y | y | Manual segmentation and complete transcription of letters. The letters sometimes differ in quality, writing colors, etc. |
| 4 | batch-04 | (97) | n | y | Segmentation and transcription of chunks of texts or unique words to help recognition form specificities: capital letters, numbers, titles, recurring elements, handwritten elements, narrow tight parts of texts |

*As there are only made for segmentation, some images/transcriptions from the "batch-00" are common with some elements founds in other corpus, but the `CONTENT` of each tag should be empty for the ALTO/PAGE XML of the "batch-00".*

*As it is made to train the transcription model on peculiar characters rendition, some images/transcriptions from the "batch-04" corpus are common with the other corpus, but the content of the XML files will differ because one will only transcribe special parts while the other will have the whole text transcribed.*

## Images
The training has been done with images digitized by the Archives départementales de la Sarthe (where the collection is kept), and then uploaded in NAKALA, which is the IIIF server used for the project that uses this corpus.  
In each folder, you can find the images with the alto files, as well as a README file that gives the link to find, in NAKALA, the images used for the training, whether it is a unique image link (for the segmentation data) or a link by letter (the name of the image is the same as the XML file).  
(Some folder in NAKALA can have more documents than what is said in the different tables because the annexes have also been uploaded in NAKALA but were often not used for the training)

## Annotation system
The corpus is made from typewritten texts so the transcription is written standardly when we have the typewritten texts.

However, there are two specificites that requires an annotation inside the transcription to have them recognize in the model that will be developed with it:
- handwritten words
- strikethrough words/parts of text

When creating our ground truth and thinking about the model we wanted to produce with it, we decided that we didn't want to train the model to recognize the handwritten parts but just to recognize thate THERE IS a handwritten part. So, every handwritten word in the ground truth is transcribed as `££` (always 2). There are as many repetition of `££` (with a space between each instance) as there are words.

In contrast, we transcribe the handwritten crossed out parts of texts (when it's readable) and we delimite them by the character `€`. One at each side, but this time, one `€`at the start of the crossed out part and one `€` at the end. Only exception: sometimes, the parts are crossed out by the machine with a capital X. In that case (and since usually only the X is readable), the text is transcribed as the X, one for each crossed out character.

## How to cite

This dataset was built and is maintained by Floriane Chiffoleau (@FloChiff). The digitization is not copyright-free, but the transcription is. However, properly annotating a corpus takes time and is a task that should be recognized. If you use any item from this corpus of ground truth, cite the dataset using the following information:

```
name: 'dahncorpus'
url: 'https://github.com/HTR-United/dahncorpus'
author: 'Floriane Chiffoleau'
month: 'march'
year: '2021'
version: '{any version}'
description: 'Ground Truth dataset for French 20th typewritten OCR'
language: 'French'
time: '1914-1924'
hands: '2'
license:
    - {name: 'CC-BY 4.0', url: 'https://creativecommons.org/licenses/by/4.0/'}
format: 'ALTO' or 'PAGE XML'
volume:
    - {count: "527", metric: pages}
```

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
