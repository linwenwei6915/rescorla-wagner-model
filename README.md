# rescorla-wagner-model
This repository contains the Stan code and accompanying Python scripts for a behavioral analysis model. The model is based on a Rescorla-Wagner learning framework and is used to analyze decision-making behavior across different conditions in a psychological experiment. The model incorporates parameters related to bias, learning rates (alpha), and choice sensitivity (beta), and accounts for trial data from multiple subjects and conditions.

### Model Overview
The Stan model (rw_mcmc.stan) is structured as follows:

#### Hierarchical Model Structure

Below is the structure of the hierarchical model used in this analysis:

![Hierarchical Model Structure](images/hierarchical_model_structure.png)


#### Data Block
The model expects data on the number of subjects, trials, and conditions, along with arrays for choice, reward, and count data.
#### Parameters Block
The model includes parameters for biases, learning rates, and choice sensitivity. These parameters are modeled with hierarchical priors to account for variability across conditions and subjects.
#### Model Block
The core of the model updates expected values (v) based on prediction errors and uses a categorical logit function to model choice probabilities.
#### Generated Quantities Block
This block calculates the log-likelihood for each subject and condition, which can be used for model comparison and evaluation.

### Data Preparation: 
Prepare your dataset according to the structure expected by the model. The data should include the choice, reward, and count information for each subject, trial, and condition.

### Fitting the Model: 
Use the provided Python script (model.py) to fit the model to your data. The script loads the data, compiles the Stan model, and runs the MCMC sampling.

```python
import pystan
posterior = stan.build(rw, data=data)
fit = posterior.sample(num_chains=nChains, num_samples=nSamples)

```

### Citation
If you use this model or the PyStan package in your research, please cite it as follows:
#### PyStan:

Stan Development Team. (2022). PyStan: The Python Interface to Stan. Retrieved from https://pystan.readthedocs.io/

### License
This project is licensed under the MIT License - see the LICENSE file for details.

### Acknowledgments
This model was developed as part of research in behavioral analysis and decision-making. Special thanks to the developers of Stan and PyStan for providing the tools to make this work possible.

Feel free to adjust the content to better suit your needs!
