the .csv file has a list of 60 patients of which the last 10 are JAX. Since the proportion of shunts in the JAX group of 30 is way larger than ours (or literature for that matter)
I randomly selected 10 of them (the only criteria beeing shunt proportion less than 40% and at least 3 measurements in the first 10 days after bleeding).
Since there was insufficient data on the BCI in the group, it is not included in the analysis

The second file, the jupyter notebook, includes the analysis, the blocks of code are more or less self explanatory
99.load the data file (after saving in locally)
100. scale/normalize data with a robust scaler (insensitive to outliers)
101. computing the statistics on the normalized set and building a dictionary holding the computed statistics (including kendall tau and sen's slope)
133. model trainig and performance eval for logistic regression (LR) and ranndom forest (RF). The choice of variables is eplanined in the comments 
but I will summarise it: I settled for these mean_cell (where cell does not include WBC) and mk_erys (kendall tau) while mk_erys and sens_erys are most likely correlated
thus introducing a multicollinearity that degrades the perfomance of the LR models. The choice for mk was based on our (Cologne) series where
the shunt proportion was more inline with the literature at large
135. finding the threshold that best separates the shunt/no shunt condition and reverse computing the raw value from the scaled data
136 and 137 SHAP plot of feature importance for the random forest
154 added an multi-layer perceptron, trained and testest on the same data, did not like the performance. the reason for importing again the libraries at the begining of the 
code block is mainly because it is transplanted form another notebook that served analysing some other data
