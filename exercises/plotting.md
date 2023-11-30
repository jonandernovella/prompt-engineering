# Prompt engineering exercises

## Creating great prompts

Example of a Vague Prompt:

**"Find information about genes related to cancer."**

Issues with the Vague Prompt:

    The prompt lacks specificity about the type of cancer or the specific information needed.
    It does not specify the criteria for determining relevance or the desired format of the information.

Example of a Well-Written Prompt:

**_"Retrieve a list of known oncogenes associated with breast cancer and provide their official gene symbols, functions, and any known interactions with therapeutic agents."_**

Advantages of the Well-Written Prompt:

    Clearly specifies the target: oncogenes.
    Provides additional context by specifying the association with breast cancer.
    Clearly outlines the information required: official gene symbols, functions, and interactions with therapeutic agents.
    This prompt is more likely to yield precise and relevant results compared to the vague prompt.

** Look at the slides to get some more tips on making your prompts more effective **

## Prompting strategies

Two-step Reasoning:

    * When to use: Use two-step reasoning when dealing with complex queries that can be logically divided into multiple steps.
    * Scenario: You suspect that your data might be contaminated and want to find possible ways to solve it
    * Example: Instead of asking the model a complex query like "Solve my issue," you can break it down into two steps: "Identify the problem in the uderlying data" and "Provide a solution." This two-step approach helps the model better understand and address the user's needs in a structured manner.

Zero-shot:

    * When to use: Use zero-shot when you want the model to generate relevant responses to queries it hasn't been explicitly trained on.
    * Scenario: you want to be first introduced to NGS
    * Example: "Please introduce me to the world of NGS"

Few-shot:

    * When to use: Use few-shot when you have a small amount of task-specific examples or prompts to guide the model's behavior.
    * Scenario: You want to make some plots and you have some different datasets belonging to different cohorts
    * Example: Instead of providing all data at once, give a few examples from your different groups so the model can generalize from them and classify them to generate better code.

## Plotting with Python using PyDataset:

In order to test the generated code, you might run it in [Google Collab](https://colab.research.google.com)

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

** Task:**

- Now, modify the prompt to filter the data for cars with more than 4 cylinders and color-code the points based on their transmission type ('am').

- Ask the chatbot to make your code more modular(using functions) and to translate to your language of choice.

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

- Now, modify the prompt to smooth the line by applying a rolling average with a window size of 5.
- Ask the bot to filter the non-binary lynx

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

- Now, modify the code to include only data points where the species is 'setosa'.
- Ask the chatbot to write some code to export the plot(s)

### Discussion

- Could you get the bot to spit out the exact same code as I pasted as examples? Did it do what you hoped for? Compare the results with other people. Is it deterministic?
- How did it go with filtering the non-binary lynx?
