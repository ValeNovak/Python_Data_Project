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


