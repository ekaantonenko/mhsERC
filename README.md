This is a code implementation of Metropolis-Hastings sampled [Ensembles of] Regressor Chains.
For any questions you can contact me via <em>ekaterina \<dot\> antonenko \<at\> minesparis \<dot\> psl \<dot\> eu</em>.

# Metropolis-Hastings sampled [Ensembles of] Regressor Chains

## Data
The folder <em> SyntheticData </em> contains a novel synthetic dataset build in this paper. 
- Feature $x$: synth_tmp_noise.csv
- Observed targets $y_{observed}$: synth_vegetation_urban.csv
- Ground-truth target values $y_{true}$: synth_vegetation_no_urban.csv

## Usage

```python

order = [0,1,2]
mdl = RegressorChain(base_estimator=RandomForestRegressor(), order=order)
mdl.fit(synthX, synthY)

### Trajectory of an RC with order [0,1,2]
tr = MHSampling(synthX, mdl, order=order)
tr012 = tr / np.sum(tr, axis=2).reshape(tr.shape[0],tr.shape[1],1)

...

### Mean trajectory of ERC
trEns = np.mean([tr012,tr021,tr102,tr120,tr201,tr210], axis=0)

```
