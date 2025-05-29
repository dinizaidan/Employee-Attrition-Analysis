# Employee Attrition Analysis

## Project Summary
This project was developed as part of a submission for the Dicoding Expert-level Data Science bootcamp, where participants are required to build end-to-end machine learning solutions using real-world workflows. Here I analyze employee attrition patterns at Jaya Jaya Maju, a fictional company, using machine learning models. The goal is to uncover key attrition drivers and provide actionable business recommendations.


## Technologies Used

| Category         | Tools/Packages                          |
|------------------|------------------------------------------|
| Development      | Python (via Conda), VSCode               |
| Modeling         | pandas, scikit-learn, matplotlib, seaborn|
| Dashboard        | Metabase                                 |
| Database         | MySQL                                    |
| Containers       | Docker, Docker Compose                   |

## Business Understanding and Problem Statement
Employee attrition is a major concern for Jaya Jaya Maju, affecting workforce stability and costs. This project aims to:
- Identify key drivers of employee attrition.
- Build predictive models.
- Visualize actionable insights through a dashboard.

## Project Scope

- Focus on supervised machine learning (Random Forest, Regression)
- Build a user-friendly dashboard with Metabase
- Use Docker to simplify deployment
- Store and query data using MySQL

Data Source: [Data Perusahaan Jaya Jaya Maju](https://raw.githubusercontent.com/dicodingacademy/dicoding_dataset/refs/heads/main/employee/employee_data.csv)

### User Installation & Setup

**Prerequisites**
- [Anaconda/Miniconda](https://docs.conda.io/en/latest/miniconda.html)
- VSCode
- Python 3.10
- Docker 
- Git

**Set up Conda environment**
```bash
conda create -n env python=3.10
conda activate env
pip install pandas scikit-learn sqlalchemy matplotlib seaborn pymysql
```

**Requirements File**
`requirements.txt` was generated after completing the project using:
```bash
pip freeze > requirements.txt
```
It includes all packages used (including conda-installed ones).

## Running the Project
Analysis workflow:
- Data Understanding
    - Preparing necessary libraries and data
    - Combining related columns (aggregations)
    - Converting several features to 'category' type
    - Dropping unnecessary columns
    - Mapping for the categories' numbers to labels
    - Visualizing numerical and categorical features
- Data Preprocesing
    - Finding and Handling Missing Values and Duplications
    - Copying data for analysis (VSCode) and Metabase
    - Preparing data for analysis (encoding, scaling, splitting)
- Modeling and Evaluation
    - Random Forest
    - Logistic Regression
    - Save the models
- Connect to MySQL

### Key Features from Random Forest
![Random Forest Feature Important Chart](image.png)

- Age and Monthly Income are top predictors.
- Rate-based compensation also influences attrition risk.


### Key Features from Logistic Regression
![Logistic Regression Chart](image-1.png)

- Higher risk attrition → Low Engagement, Job level 5, Tech Degree
- Lower risk attrition → Very High Engagement, Job Level 2, Human Resource, Low Work Pressure

## Metabase Application

**Start Docker Containers**
```bash
docker-compose up
```
MySQl is accessible on port `3306`
Metabase dashboard is accessible on `http://localhost:3000`

### Connecting to MySQL

1. Create a SQLAlchemy engine:
```python
from sqlalchemy import create_engine
engine = create_engine('mysql+pymysql://username:password@localhost:3306/database_name')
```

2. Save data to MySQL
```python
table_name = 'employee'
employee_dashboard.to_sql(table_name, con=engine, if_exists='replace', index=False)
```

### Dashboard Overview 
![Dashboard Overview](image-2.png)

- Young employees (22–37.5) dominate attrition.
- High engagement doesn’t always equate to retention.
- R&D department and male/single employees show higher attrition.


## Conclusions & Recommendations

### Conclusion

In summary, the predictive models highlight key attrition drivers such as age, monthly income, and engagement level, while descriptive analysis reveals demographic patterns like young, single, male employees in R&D being most affected.

Interestingly, some high-risk groups (e.g., those with “High Engagement”) also had high attrition counts, suggesting that raw numbers don’t always align with true risk factors. This reinforces the importance of using both statistical modeling and descriptive summaries to gain a complete picture.

To reduce attrition effectively, organizations should blend data-driven modeling insights with on-the-ground HR strategies tailored to actual departing employee profiles.

### Recommendations
- **Target Age Group (30–37.5)**
Provide career development programs and mentorship to reduce uncertainty and increase loyalty.

- **Align Compensation Expectations**
Pair raises with recognition and role clarity to avoid perceived unfairness.

- **Monitor Engagement Holistically**
High engagement could mask burnout. Measure stress and support as well.

## Contact
For any questions or feedback:
dininadwah@gmail.com
'https://www.linkedin.com/in/dznadwah/'
>>>>>>> 32b4aa1 (Initial project upload)
