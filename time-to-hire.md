# dataviz
import pandas as pd
import pylab as plt
import numpy as np

T2Hfile = pd.ExcelFile('/Users/USER/Downloads/time-to-hire-data-file.xlsx')
T2Hfile
T2Hfile.sheet_names

df = T2Hfile.parse('TimetoHire1-15-2010 (1)') 
df

df['RECEIVED_DATE'].isnull().value_counts()
df['HIRED_DATE'].isnull().value_counts()
df['HIRE_COUNT'].isnull().value_counts()
np.mean(df['HIRE_COUNT'])

T2H_days = pd.Series(delta.days for delta in (df['HIRED_DATE'] - df['RECEIVED_DATE']))
np.mean(T2H_days)
np.max(T2H_days)
np.std(T2H_days)
np.var(T2H_days)

HIRED_DATE_CY = df['HIRED_DATE'].dt.year
HIRED_DATE_CY

### crosstab - https://chrisalbon.com/python/pandas_crosstabs.html
pd.crosstab(HIRED_DATE_CY, df['HIRE_COUNT'], margins=True)
