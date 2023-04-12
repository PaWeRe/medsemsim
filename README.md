# Medical Semantic Similarity Matcher

When curating medical data we often face slightly different descriptions of the same medical entities / terms. These variations while often-times breaking carefully designed regular expressions or basic string comparison operations (often times also requiring a significant amount of preprocessing, in terms of cleaning and standardization) do not change the semantic meaning of the terms (e.g. "LEFT TRANSITION ZONE ANTERIOR MID APEX" and	"A. LEFT TRANSITION ZONE ANTERIOR MID TO APEX, PROSTATE BIOPSIES" refer to the same anatomical region of the prostate).

## Method
For using the semantics for matching, the following simple method is used:
1. Extract target keyword and candidate keywords from clinical report or clinical entity (using basic nlp techniques, like regex, tokenization, etc.)
2. Project candidates and targety kewyord in joint vector space, by vectorizing keywords with publicly available pre-trained DL-based models (e.g. [bio_clinicalBERT](https://huggingface.co/emilyalsentzer/Bio_ClinicalBERT) from Hugging Face) 
3. Apply similarity metric to compute distance scores between all candidates and the target keyword (e.g. cosine-similarity)
4. Define threshold and match candidate with best score to target keyword
5. Re-iterate for increasing accuracy (e.g. better extraction of candidates, try out different pre-trained models (maybe even fine-tuning possible if sufficient data + labels are given), try out different similarity metrics and different thresholds, etc.)

## Use case 1: Matching anatomical regions of the prostate for matching pathology report diagnoses from prostate biopsies with image regions or targets

## Use case 2: Matching manually-inputted Seriesdescription of medical images with DICOM metadata 

## Installation
Either clone repository or use pip install it with following command:

## Disclaimer
... Feel free to share issues or improvements as issues or PRs :)

