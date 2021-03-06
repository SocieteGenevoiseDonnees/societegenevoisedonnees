---
layout: support-page
title: Data visualisation with matplotlib
tags: [python, matplotlib, visualisation]
---

```python
import pandas as pd
import numpy as np
```

read in some data


```python
filename = "data/percent-bachelors-degrees-women-usa.csv"
data = pd.read_csv(filename, usecols=['Year','Computer Science','Physical Sciences','Health Professions','Education'])
data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Computer Science</th>
      <th>Education</th>
      <th>Health Professions</th>
      <th>Physical Sciences</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1970</td>
      <td>13.6</td>
      <td>74.535328</td>
      <td>77.1</td>
      <td>13.8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1971</td>
      <td>13.6</td>
      <td>74.149204</td>
      <td>75.5</td>
      <td>14.9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1972</td>
      <td>14.9</td>
      <td>73.554520</td>
      <td>76.9</td>
      <td>14.8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1973</td>
      <td>16.4</td>
      <td>73.501814</td>
      <td>77.4</td>
      <td>16.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1974</td>
      <td>18.9</td>
      <td>73.336811</td>
      <td>77.9</td>
      <td>18.2</td>
    </tr>
  </tbody>
</table>
</div>




```python
import matplotlib.pyplot as plt
```

First we extract the numpy arrays holding the data


```python
years = data['Year'].values
physical_sciences = data['Physical Sciences'].values
computer_science = data['Computer Science'].values
education = data['Education'].values
health = data['Health Professions'].values
```


```python
# % of degrees awarded to women in the Physical Sciences
plt.plot(years, physical_sciences, color='blue', marker='.')

# % of degrees awarded to women in Computer Science
plt.plot(years, computer_science, color='red')

# Display the plot
plt.show()
```


![png](/assets/StepFive-Plotting/output_6_0.png)


Make 2 plots side by side


```python
# plot axes for the first line plot
plt.axes([0.05, 0.05, 0.425, 0.9])

# % of degrees awarded to women in the Physical Sciences
plt.plot(years, physical_sciences, color='blue')

# plot axes for the second line plot
plt.axes([0.525, 0.05, 0.425, 0.9])

# % of degrees awarded to women in Computer Science
plt.plot(years, computer_science, color='red')

# Display the plot
plt.show()
```


![png](/assets/StepFive-Plotting/output_8_0.png)



```python
# Create a figure with 1x2 subplot and make the left subplot active
plt.subplot(1,2,1)

# % of degrees awarded to women in the Physical Sciences
plt.plot(years, physical_sciences, color='blue')
plt.title('Physical Sciences')

# Make the right subplot active in the current 1x2 subplot grid
plt.subplot(1,2,2)

# % of degrees awarded to women in Computer Science
plt.plot(years, computer_science, color='red')
plt.title('Computer Science')

# Use plt.tight_layout() to improve the spacing between subplots
plt.tight_layout()
plt.show()
```


![png](/assets/StepFive-Plotting/output_9_0.png)



```python
# Create a figure with 2x2 subplot layout and make the top left subplot active
plt.subplot(2,2,1)

# Plot in blue the % of degrees awarded to women in the Physical Sciences
plt.plot(years, physical_sciences, color='blue')
plt.title('Physical Sciences')

# Make the top right subplot active in the current 2x2 subplot grid 
plt.subplot(2,2,2)

# Plot in red the % of degrees awarded to women in Computer Science
plt.plot(years, computer_science, color='red')
plt.title('Computer Science')

# Make the bottom left subplot active in the current 2x2 subplot grid
plt.subplot(2,2,3)

# Plot in green the % of degrees awarded to women in Health Professions
plt.plot(years, health, color='green')
plt.title('Health Professions')

# Make the bottom right subplot active in the current 2x2 subplot grid
plt.subplot(2,2,4)

# Plot in yellow the % of degrees awarded to women in Education
plt.plot(years, education, color='yellow')
plt.title('Education')

# Improve the spacing between subplots and display them
plt.tight_layout()
plt.show()
```


![png](/assets/StepFive-Plotting/output_10_0.png)



```python
# % of degrees awarded to women in the Physical Sciences
plt.plot(years, physical_sciences, label='physical sciences', color='blue')

# % of degrees awarded to women in Computer Science
plt.plot(years, computer_science, label='computer science', color='red')

# Display the plot
plt.legend(fontsize=20)
plt.xlabel("year")
plt.ylabel('number of degrees awarded')
plt.show()
```


![png](/assets/StepFive-Plotting/output_11_0.png)


## Plotting directly with Pandas!


```python
data.plot(x="Year")
plt.ylabel("number of degrees awarded")
plt.show()
```


![png](/assets/StepFive-Plotting/output_13_0.png)

[back to edition]({% post_url 2018-06-14-Getting-Started %})