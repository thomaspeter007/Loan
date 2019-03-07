# Loan
#To find a customer eligible for loan or not
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("L1.csv")
df1=pd.read_csv("L2.csv",engine='python')
df.apply(lambda x: sum(x.isnull()))
k=[x for x in df.columns if sum(df[x].isnull())>20000]
df=df.drop(columns=k)
