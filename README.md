# Project Overview

This is my first data analysis project, where I primarily focused on learning new skills for a Data Analyst role. I followed the "Python for Data Analytics - Full Course for Beginners" by Luke Barousse on YouTube, which helped me improve my Python skills. Before that, I learned Python from the book "Think Python" by Allen B. Downey.

For this project, I analyzed skills, salaries, and job demand in the data analytics field. Initially, I wanted to work with data for Croatia, but I found that the available data was too limited and lacked depth. Because of this, I decided to continue my analysis using data from the United States, where information is more detailed and widely available.

However, I still included some analysis for Croatia where possible, to compare and explore differences. This project helped me practice data cleaning, visualization, and insights extraction while improving my Python skills for data analysis.

# The Questions

Below are the questions I want to answer in my project:
    
    1. What are the skills most in demand for the top 3 most popular data roles?
    2. How are in-demand skills trending for Data Analysts?
    3. How well do jobs and skills pay for Data Analysts?
    4. What are the optimal skills for data analysts to learn? (High Demand and High Paying)

# Tools I Used

For this analysis, I primarily used Python along with several key libraries for data manipulation and visualization:

- Pandas – for data cleaning, manipulation, and exploration
- Matplotlib – for basic data visualization
- Seaborn – for advanced and more visually appealing statistical plots

I ran my Python scripts using Jupyter Notebook, which allowed for interactive coding and analysis. Additionally, I used Visual Studio Code for executing scripts and general coding.

For version control and sharing my work, I utilized Git and GitHub, ensuring proper tracking of changes and collaboration.


# The Analysis

## 1. What are the most demanded skills fot the top 3 most popular data roles?


To find the most demanded skills fot the top 3 most popular data roles. I filtered out those position by which ones were the most popular, and got the top 5 skills for these top 3 roles in Croatia. This query highlights the most popular job titles and their top skills, showing which skills I shoud pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [2_Skill_Demand.ipynb](3_Project\2_Skill_Demand.ipynb)

## Visualize Data

```python
for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_perc', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')

plt.show()
```

### Results

![Visualization of Top Skills in Croatia](https://github.com/ValeNovak/Python_Data_Project/blob/main/3_Project/images/skill_demand_all_data_roles.png)

*Top skills requested in Croatia Job Postings*



### Insights

This visualization highlights the most in-demand skills for three job roles in Croatia: Data Analyst, Data Engineer, and Data Scientist.

- SQL is the most requested skill across all roles, particularly for Data Engineers (70%) and Data Scientists (55%).
- Python is also highly valued, especially for Data Scientists (71%) and Data Engineers (69%).
- Cloud and workflow tools such as AWS, Azure, and Airflow are relevant for Data Engineers.
- BI and visualization tools like Power BI and Tableau are important for Data Analysts.
- Deep learning frameworks like PyTorch and TensorFlow appear prominently for Data Scientists.

These insights can help job seekers prioritize their learning based on role-specific skill demand.


## 2. How are in-demand skills trending for Data Analysts?

View my notebook with detailed steps here: [3_Skill_Trends.ipynb](3_Project\3_Skill_Trends.ipynb)

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

![Trendig Top Skills for Data Analysts in th US](https://github.com/ValeNovak/Python_Data_Project/blob/main/3_Project/images/Trending_top_skills_DA_US.png)

*Bar graph visualizing the trending top skills for data analysts in the US 2023.*


### Insights

-SQL remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.
- Excel experienced a significant increase in demand starting around September, surpassing both Python and Tableau by the end of the year.
-Both Python and Tableau show relatively stable demand throughout the year with some fluctuations bur remain essential skills for data analysts. Power BI, while less demanded compared to the others, shows a slight upward trend towards the year's end.

## 3. How well do jobs and skills pay for Data Analysts?

View my notebook with detailed steps here: [4_Salary_Analysis.ipynb](3_Project\4_Salary_Analysis.ipynb)


## Salary Analysis

#### Visualize Data

```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short', order=job_order)

ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'${int(x/1000)}K'))

```
#### Results

![Salary  Distriburions of Data Jobs in th US](https://github.com/ValeNovak/Python_Data_Project/blob/main/3_Project/images/Salary_distributions_US.png)

*Box plot visualizing the salary distributions for the top 6 data job titles.*

#### Insights

This boxplot visualizes the salary distribution for various data-related roles in the United States, including Data Analyst, Senior Data Analyst, Data Engineer, Senior Data Engineer, Data Scientist, and Senior Data Scientist.

Each box represents the interquartile range (IQR), showing the middle 50% of salaries for each role. The line inside the box indicates the median salary, while the whiskers extend to capture most of the data, excluding extreme outliers. The dots beyond the whiskers represent outliers—salaries that are significantly higher or lower than the majority.

Key insights from the graph:

- Higher seniority = higher salaries: Senior roles tend to have higher median salaries and larger salary ranges.
- Data Scientists and Data Engineers have similar distributions, but Senior Data Scientists have the highest median pay.
- Significant outliers exist, especially in senior roles, indicating that some professionals earn exceptionally high salaries.
- Data Analysts have the lowest salary range, with less variation compared to other roles.

This visualization helps understand salary trends and variations in the data industry, highlighting differences between positions and experience levels.

### Highest Paid & Most Demanded Skills for Data Analysts



#### Visualize Data

```python 

#Top 10 Highest Paid Skills fot Data Analysts
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, ax=ax[0],hue='median', palette='dark:b_r')

#Top 10 Most In-Demand Skills fot Data Analysts
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, ax=ax[1], hue='median', palette='light:b')

plt.show()
```

#### Results 

![The Highest Paid & Most In-Demand Skills for Data Analysts in the US](https://github.com/ValeNovak/Python_Data_Project/blob/main/3_Project/images/Salary_DA.png)

*Two separate bar graphs visualizing the highest paid skills and most in-demand skills for data analysts in the US.*

### Insights

- The top graph shows specialized technical skill like 'dplyr', 'Bitbucket' and 'Gitlab' are assoiciated with higher salaries. 

- The bottom graph highlights that fundational skills like 'Excel', 'Python' and 'SQL' are most in-demand even though they may not offer the highest salaries.

## 4. What is the most optimal skill to learn for Data Analysts?

Let's check out in Luke's code that I'm learning from.

View my notebook with detailed steps here: [5_Optimal_skills.ipynb](3_Project\5_Optimal_skills.ipynb)

#### Visualize Data

```python
sns.scatterplot(
    data=df_plot,
    x='skill_percent',
    y='median_salary',
    hue='technology'
)
sns.despine()
```

#### Results

![Optimal skills](https://github.com/ValeNovak/Python_Data_Project/blob/main/3_Project/images/Optimal_skills.png)

*A scatter plot visualizing th most optimal skills (high paying & high demand) for data analysts in the US.*


#### Insights


This scatter plot shows the most valuable skills for data analysts in the US, based on job demand and median yearly salary.

- X-axis: Percentage of job postings requiring each skill (demand).
- Y-axis: Median yearly salary for roles requiring that skill.
- Color-coded categories: Programming (blue), Analyst Tools (orange), Databases (green), and Cloud (red).

Key Insights:
- SQL is the most in-demand skill (~55% of jobs) and Python offers one of the highest salaries ($98K). 
- Tableau, Power BI, and R are valuable analytical tools with solid salaries.
- Excel is widely used (~40% demand) but offers lower salary potential.
- Cloud and database skills (Oracle, SQL Server) pay well but have lower demand.

Overall, programming and database skills (Python & SQL) are the most valuable for data analysts in terms of both salary and demand.

## What I’ve Learned

Building upon the foundation provided by the book "Learn Python," this project has significantly enhanced my understanding of Python, especially in the areas of libraries, data cleaning, and strategy analysis. Working on this project, I’ve encountered and tackled numerous new concepts that have broadened my skill set. The hands-on experience with libraries has been invaluable, allowing me to explore and apply various tools that are crucial for data analysis and processing. Data cleaning, which initially seemed like a daunting task, has become more intuitive, and I now feel confident in handling messy datasets. Furthermore, diving into strategy analysis has given me insights into how data can be used to drive decision-making.

This project has been an incredible learning opportunity, and it has inspired me to continue growing in these areas. I am excited to further develop my skills in Python and explore even more advanced techniques in the future.

