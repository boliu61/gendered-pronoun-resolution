solution write-up is at: https://www.kaggle.com/c/gendered-pronoun-resolution/discussion/90334

paper is at: https://arxiv.org/abs/1905.01780

## File descriptions

* `Step1_preprocessing.ipynb` given [dev, test, val, stage2] input tsv files, generate augmented tsv; extract bert features jsons, distance features, and linguistic features, saved to Drive
* `Step2_end2end_model.ipynb` from [dev, test, val, stage2] features saved in step 1, train "end2end" model and save weights (250 for sub_A and 50 for sub_B) -- only used for training
* `Step3_pure_bert_model.ipynb` from [dev, test, val, stage2] features saved in step 1, train "pure bert" model and save weights (50 for sub_A and 50 for sub_B) -- only used for training
* `Step4_inference.ipynb` using saved features in step1 and saved weigths in step2 and 3, do inference

*  `gap-development-corrected-74.tsv` dev input file with 74 wrong labeled fixed -- only used for training
*  `gap-test-val-85.tsv` test and val input file (combined) with 85 wrong labeled fixed -- only used for training

## Training insturctions
1. Run `Step1_preprocessing.ipynb` to generate augmented tsv files and extract features for dev, test and val 
2. Run `Step2_end2end_model.ipynb` to train the "end2end" model and save weights
3. Run `Step3_pure_bert_model.ipynb`  to train the "pure bert" model and save weights

Both step2 and 3 need to be ran 4 times, with `all_train = True` and `False`, and `CASED = False` and `True` respectively. Step2 and 3 will generate 5.11G weights files in total.

## Inference instructions
1. Run `Step1_preprocessing.ipynb` to extract features for stage2 data
2. Run `Step4_inference.ipynb` twice to do inference for both subissions: `all_train=True` for sub_A, `all_train=False` for sub_B
