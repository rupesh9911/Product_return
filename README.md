import pandas as pd

df = pd.read_excel("return_analysis_report.xlsx")
df.head()


import seaborn as sns
import matplotlib.pyplot as plt

cat_return = df.groupby('Category')['Returned'].mean() * 100
cat_return.plot(kind='bar', color='skyblue')
plt.title("Return % by Category")
plt.ylabel("Return %")
plt.show()



top_products = df[df['Returned'] == 1]['Product'].value_counts()
top_products.plot(kind='bar', color='orange')
plt.title("Most Returned Products")
plt.ylabel("Return Count")
plt.show()


sns.heatmap(df[['Price', 'Quantity', 'Returned']].corr(), annot=True, cmap="coolwarm")
plt.title("Correlation Heatmap")
plt.show()
