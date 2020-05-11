## readme 

This gist contains the code for the DIET benchmarking. 🔥🔥🔥🔥

If you don't already have it, install [rasa](https://rasa.com/docs/rasa/user-guide/installation/).

You will need to ensure that you've installed the BERT dependencies if you
want to run the heavy model. 

```
pip install "rasa[transformers]"
```

After downloading this repo, move the directory **configs** and the file **viewresults.py** to the root directory of your rasa project.

Once that is done you can evaluate all of the configurations by running from the root directory of your project; 

```
mkdir results
rasa test nlu --config configs/config-orig.yml --cross-validation --runs 1 --folds 2 --out results/config-orig
rasa test nlu --config configs/diet-replace-mask.yml --cross-validation --runs 1 --folds 2 --out results/diet-replace-mask
rasa test nlu --config configs/diet-replace.yml --cross-validation --runs 1 --folds 2 --out results/diet-replace
rasa test nlu --config configs/diet-light.yml --cross-validation --runs 1 --folds 2 --out results/diet-light
rasa test nlu --config configs/diet-heavy.yml --cross-validation --runs 1 --folds 2 --out results/diet-heavy
rasa test nlu --config configs/config-mega-basic.yml --cross-validation --runs 1 --folds 2 --out results/config-mega-basic
rasa test nlu --config configs/old_turnero.yml --cross-validation --runs 1 --folds 2 --out results/old_turnero
rasa test nlu --config configs/asisto_covid.yml --cross-validation --runs 1 --folds 2 --out results/asisto_covid
```

Once this is finished, you can use streamlit to see this nifty dashboard of the results. 

```
pip install streamlit
streamlit run viewresults.py
```
It should give you some graphs like this:

![dataviz_example](example_visualization.png "example data viz")

NOTE: If you want to see the evaluation of **entities** uncomment the code at the bottom of **viewresults.py**.

Also, here is a great [YouTube tutorial](https://youtu.be/oj5oPGDlep4) by vincent d warmerdam, where I took the code for this benchmarking.