# covid-data-visualization-using-live-data
# Importing the necessary libraries to run the code in jupyter notebook
import pandas as pd
  
import plotly.graph_objs as go
# Live data available from oxford covid policy tracker is uploaded (https://github.com/OxCGRT/covid-policy-tracker)
count_df = pd.read_csv('https://raw.githubusercontent.com/OxCGRT/covid-policy-tracker/master/data/OxCGRT_latest.csv')
count_df.head()
# Getting UK data
count_df = count_df[(count_df["CountryName"]=="United Kingdom") & (count_df['RegionCode'].isna())]

count_df.head()
# Getting the number of deaths and cases
count_df = count_df.drop(['CountryName', 'CountryCode', 'RegionName', 'RegionCode'], axis=1).set_index('Date').fillna(method='ffill')

uk_df = count_df[["ConfirmedCases", "ConfirmedDeaths"]]

uk_df.index = pd.to_datetime(uk_df.index, format="%Y%m%d")

uk_df
# Calculating the infection rate and calculating by date
uk_df.head()

uk_df.index = pd.to_datetime(uk_df.index, format="%Y%m%d")

uk_df = uk_df.sort_index()

uk_df
# Visualizing the case and death count of UK in plotly
fig = go.Figure()

for col in uk_df[['ConfirmedCases', 'ConfirmedDeaths']]:
    
fig.add_trace(go.Scatter(x=uk_df.index, y=uk_df[col], name=col))    

fig.update_layout(title="Case & Death Count in UK")
# Visualizing the infection rate of UK in plotly
fig = go.Figure()

for col in uk_df[['InfectionRate']]:

fig.add_trace(go.Scatter(x=uk_df.index, y=uk_df[col], name=col)) 

fig.update_layout(title="Infection Rate in UK")
