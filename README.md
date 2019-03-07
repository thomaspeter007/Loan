import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("L1.csv")
#df1=pd.read_csv("L2.csv",engine='python')
df.apply(lambda x: sum(x.isnull()))
k=[x for x in df.columns if sum(df[x].isnull())>20000]
df=df.drop(columns=k)
df=df[(df["loan_status"]=='Fully Paid')| (df["loan_status"]=='Charged Off')]
df.head()
df.loan_status.replace({'Fully Paid':1,"Charged Off":0},inplace=True)
df=df.loc[:,df.apply(pd.Series.nunique)!=1]
# remove data have null values
df=df.loc[:,(df.isnull().sum()) < 100]
df=data.dropna(axis=0)
convert % object to int
df.int_rate=df.int_rate.str.rstrip('%').astype("float64")
df.revol_util=df.revol_util.str.rstrip('%').astype("float64")
x=df.loan_status.value_counts().index
y=df.loan_status.value_counts().values
plt.bar(x, y, width=.25, align='center')
plt.xticks(x)
plt.yticks(y)
plt.show()
