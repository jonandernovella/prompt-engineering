# Prompt engineering exercises

In order to test the generated code, you might run it in [Google Collab](https://colab.research.google.com)

## Plotting with Python using PyDataset:

### 1. Scatter Plot

**Prompt:**
Generate Python code to create a scatter plot using the 'mtcars' dataset from `pydataset`. Plot the relationship between horsepower ('hp') and miles per gallon ('mpg'). Include labels for the axes and a title. Bonus points for adding color-coded data points based on the number of cylinders.

**Example Solution:**

```python
import matplotlib.pyplot as plt
from pydataset import data

mtcars = data('mtcars')
plt.scatter(mtcars['hp'], mtcars['mpg'], c=mtcars['cyl'], cmap='viridis')
plt.xlabel('Horsepower')
plt.ylabel('Miles per Gallon')
plt.title('Scatter Plot of Horsepower vs. MPG')
plt.colorbar(label='Number of Cylinders')
plt.show()
```

**Task:**
Now, modify the prompt to filter the data for cars with more than 4 cylinders and color-code the points based on their transmission type ('am').

### 2. Line Chart

**Prompt:**
Provide Python code to generate a line chart using the 'lynx' dataset from `pydataset`. Plot the number of lynx trapped ('lynx') over time ('time'). Ensure the plot is visually appealing with appropriate annotations.

**Example Solution:**

```python
import matplotlib.pyplot as plt
from pydataset import data

lynx = data('lynx')
plt.plot(lynx['time'], lynx['lynx'], marker='o')
plt.xlabel('Time')
plt.ylabel('Number of Lynx Trapped')
plt.title('Lynx Population Over Time')
plt.grid(True)
plt.show()
```

**Task:**
Now, modify the prompt to smooth the line by applying a rolling average with a window size of 5.

### 3. Heatmap

**Prompt:**
Write Python code to generate a heatmap using the 'iris' dataset from `pydataset`. Create a heatmap of the correlation matrix between sepal length, sepal width, petal length, and petal width. Ensure the visualization is informative.

**Example Solution:**

```python
import seaborn as sns
from pydataset import data

iris = data('iris')
correlation_matrix = iris[['Sepal.Length', 'Sepal.Width', 'Petal.Length', 'Petal.Width']].corr()
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Heatmap of Correlation Matrix (Iris Dataset)')
plt.show()
```

**Task:**
Now, modify the code to include only data points where the species is 'setosa'.
