# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
## Date: 
## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
## PROGRAM:
```
Name : MANOJ G
Reg no : 212222240060
```
### REGULAR DIFFERENCING
```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
data=pd.read_csv("/content/astrobiological_activity_monitoring.csv",parse_dates=['Date'],index_col='Date')
data.head()
passengers = pd.DataFrame(data)
passengers['shifted_value']=passengers['Atmospheric_Composition_O2'].shift(1)
passengers['difference_value']=passengers['Atmospheric_Composition_O2']-passengers['shifted_value']
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### SEASONAL ADJUSTMENT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv("/content/astrobiological_activity_monitoring.csv",parse_dates=['Date'],index_col='Date')
passengers=pd.DataFrame(data)
result=seasonal_decompose(passengers['Atmospheric_Composition_Methane'],model='additive',period=1)
seasonal=result.seasonal
passengers['Seasonal_value']=passengers['Atmospheric_Composition_Methane']-seasonal
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### LOG TRANSFORMATIONS
```
import numpy as np
import pandas as pd
data= pd.read_csv('/content/astrobiological_activity_monitoring.csv')
data.head()
data.dropna(inplace=True)
x=data['Date']
y=data['Human_Activity_Metrics']
data_log=np.log(data['Human_Activity_Metrics'])
X=data['Date']
Y=data_log
import matplotlib.pyplot as plt
plt.plot(x,y)
plt.xlabel('Original Data')
plt.plot(X,Y)
plt.xlabel('Log- Transformed data')
```

## OUTPUT:
### REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/f29eaf4b-e85e-4bbb-bf0f-56efab39070a)

### SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/cbe2df99-3837-4c20-b77d-615ed54e6ad6)

### LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/e7d452e9-687a-4a8f-a537-788dc8b0f3dc)


## RESULT:
Thus , This is the python code for the conversion of non stationary to stationary data.
