# The Analysis

## 1. What are the most demanded skills fot the top 3 most popular data roles?


To find the most demanded skills fot the top 3 most popular data roles. I filtered out those position by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I shoud pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [2_Skill_Demand.ipynb](3_Project\2_Skill_Demand.ipynb)

## Visualize Data

```python
for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_perc', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')

plt.show()
```

### Results

![Visualization of Top Skills in Croatia](3_Project\images\skill_demand_all_data_roles.png)

### Insights

This visualization highlights the most in-demand skills for three job roles in Croatia: Data Analyst, Data Engineer, and Data Scientist.

- SQL is the most requested skill across all roles, particularly for Data Engineers (70%) and Data Scientists (55%).
- Python is also highly valued, especially for Data Scientists (71%) and Data Engineers (69%).
- Cloud and workflow tools such as AWS, Azure, and Airflow are relevant for Data Engineers.
- BI and visualization tools like Power BI and Tableau are important for Data Analysts.
- Deep learning frameworks like PyTorch and TensorFlow appear prominently for Data Scientists.

These insights can help job seekers prioritize their learning based on role-specific skill demand.


## 2. How are in-demand skills trending for Data Analysts?

### Visualize Data

```python

df_plot = df_DA_US_percent.iloc[:, :5]

sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

from matplotlib.ticker import PercentFormatter
ax=plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i])


plt.show()
```

### Results

![Trendig Top Skills for Data Analysts in th US](3_Project\images\Trending_top_skills_DA_US.png)
*Bar graph visualizing the trending top skills for data analysts in the US 2023.*


### Insights

-SQL remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.
- Excel experienced a significant increase in demand starting around September, surpassing both Python and Tableau by the end of the year.
-Both Python and Tableau show relatively stable demand throughout the year with some fluctuations bur remain essential skills for data analysts. Power BI, while less demanded compared to the others, shows a slight upward trend towards the year's end.

## 3. How well do jobs and skills pay for Data Analysts?

## Salary Analysis

#### Visualize Data

```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short', order=job_order)

ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'${int(x/1000)}K'))

```
#### Results

![Salary  Distriburions of Data Jobs in th US](3_Project\images\Salary_distributions_US.png)*Box plot visualizing the salary distributions for the top 6 data job titles.*

#### Insights

This boxplot visualizes the salary distribution for various data-related roles in the United States, including Data Analyst, Senior Data Analyst, Data Engineer, Senior Data Engineer, Data Scientist, and Senior Data Scientist.

Each box represents the interquartile range (IQR), showing the middle 50% of salaries for each role. The line inside the box indicates the median salary, while the whiskers extend to capture most of the data, excluding extreme outliers. The dots beyond the whiskers represent outliers—salaries that are significantly higher or lower than the majority.

Key insights from the graph:

- Higher seniority = higher salaries: Senior roles tend to have higher median salaries and larger salary ranges.
- Data Scientists and Data Engineers have similar distributions, but Senior Data Scientists have the highest median pay.
- Significant outliers exist, especially in senior roles, indicating that some professionals earn exceptionally high salaries.
- Data Analysts have the lowest salary range, with less variation compared to other roles.

This visualization helps understand salary trends and variations in the data industry, highlighting differences between positions and experience levels.



