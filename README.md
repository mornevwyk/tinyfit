![PyPI - License](https://img.shields.io/pypi/l/tinyfit) ![PyPI - Downloads](https://img.shields.io/pypi/dm/tinyfit)

# tinyfit
A small, light-weight python regression library.

## Usage
### Instalation
```
$ py pip install tinyfit
```

### Data fitting and scaling
For linear regression models import linreg and create a new LinearRegression object. Also import scaling for feature scaling.
```python
import tinyfit.linreg as lreg
import tinyfit.scaling as sc

lr = lreg.LinearRegression()
```

Create a test data set
```python
n = 200
rand = np.random.normal(0,5,n)
x_values = np.random.normal(100,20,n)
y_values = 10 + x_values + rand

#scale features
x_values = sc.minmax(x_values)
```

Set learning rate of model and fit to data
```python
lr.lr = 0.001
lr.fit(x_values, y_values, iter=1000)
```

Make predictions using predict()
```
vals = np.array([1,2,3,4,5])
pred = lr.predict(vals)
```

For linear regression with multiple features
```python
lr = lreg.LinearRegression(n_features = 2) # set n_features to the number of expected features (2 in this example)
scaler = sc.FeatureScaler() # set up the auto-scaler
scaler.scale_types = ['meannorm']*2 # set the scaling needed for each feature in the dataset

x_values = scaler.scale(x_values) # scale features (x_values must be a 2xn np.array in this example)
lr.fit(x_values, y_values, iter=1000) # fit to data

pred = lr. pred(vals)
```
