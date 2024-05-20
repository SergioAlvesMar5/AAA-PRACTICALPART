# GLAD: Groningen Lightweight Authorship Detection 

## Example uses of `glad-main.py` ##
In the following examples the following placeholders are used to have shorter commands (this assumes the PAN2014/15 datasets are downloaded):

`$trainingDataset`:   `C:\Users\HP\git\AAA-practicalpart\pan15-authorship-verification-training-dataset-english-2015-04-19`

`$inputDataset`:   `C:\Users\HP\git\AAA-practicalpart\pan14-author-verification-test-corpus2-english-novels-2014-04-22`

`$modelDir`:   `C:\Users\HP\git\AAA-practicalpart\example_model`

`$answersDir`:   `C:\Users\HP\git\AAA-practicalpart\answers`

### Train a model ###

`python3 glad-main.py --training $trainingDataset -i $inputDataset --save_model $modelDir`
>  `--training` Use this data set to train a model
> 
>  `--save_model` Store the model to this directory. If the directory already exists, it will write anyways (and update).


### Make predictions using an existing model ###

`python3 glad-main.py -i $inputDataset -m $modelDir`
>  `-m` Load the model; alternative flag: `--model`
> 
> `-i` make predictions on the `$inputDataset`; alternative flags: `--test` `--input` 

### Train and test a model ###
`python3 glad-main.py --training $trainingDataset --test $inputDataset`
>  `--training` Use this data set to train a model
>
> `--test` make predictions on the `$inputDataset`; alternative flags: `-i` `--input`

`python3 glad-main.py --training $trainingDataset --split`
>  `--training` Use this data set to train a model
>
> `--split` split on the training data. Default split: 70%. Define your own split like this: `--split 0.5`

### Writing the predictions ###

`python3 glad-main.py -i $inputDataset -m $modelDir -o $answersDir`
> `-o` store the *answers.txt* file to the directory `$answersDir`; alternative flag: `--out`

`python3 glad-main.py -i $inputDataset -m $modelDir -a path/to/answers.file`
> `-a` store the predictions to a file; alternative flag: `--answers`


### Using the crossvalidation ###
`python3 glad-main.py --training $trainingDataset --cv [k]`
> `--cv` "Perform stratified cross validation on the training data. Takes an optional int "
                                 "specifying the number of folds to perform. (Default k=10)"; alternative flag: "--cross-validation"


### Using the classifier ###
`python3 glad-main.py --training $trainingDataset --c [classifier]`
> `--c` "all available classifiers
                "svm", "Support Vector Machine"
                "svm_gs1", "Co-best SVM according to Skll Grid Search",
                "svm_gs2", "Co-best SVM according to Skll Grid Search",
                "mnb", "Multinomial Naive Bayes"
                "knn", "k Nearest Neighbour"
                "raf", "Random Forest",
                 alternative flag: "--classifier"


## Requirements ##

- Python 3.x
- NLTK 
- NumPy
- scikit-learn
- (liac-arff)
