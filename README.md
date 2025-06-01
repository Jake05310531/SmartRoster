# SmartRoster

SmartRoster is a sports analytics and finance project designed to analyze player and team statistics and generate data-driven performance grades. Inspired by Moneyball concepts, it aims to help fans, analysts, and fantasy sports players make smarter decisions using advanced stats and financial analysis.

## Features

- Aggregate multiple player stats into a single overall grade  
- Display detailed sub-stats for transparency  
- Incorporate salary data to weigh performance against cost  
- Interactive Jupyter notebooks for easy experimentation  

## Example Usage

Here’s a simple example of how SmartRoster calculates player grades based on their stats and salary:

```python
import pandas as pd

data = {
    'Player': ['Alice', 'Bob', 'Charlie'],
    'Points Per Game': [25, 18, 22],
    'Rebounds Per Game': [8, 10, 7],
    'Assists Per Game': [5, 7, 4],
    'Salary ($M)': [15, 12, 9]
}

df = pd.DataFrame(data)

def normalize(series):
    return (series - series.min()) / (series.max() - series.min())

df['Points_norm'] = normalize(df['Points Per Game'])
df['Rebounds_norm'] = normalize(df['Rebounds Per Game'])
df['Assists_norm'] = normalize(df['Assists Per Game'])
df['Salary_norm'] = normalize(df['Salary ($M)'])

df['Overall Grade'] = (
    df['Points_norm'] * 0.4 +
    df['Rebounds_norm'] * 0.3 +
    df['Assists_norm'] * 0.2 -
    df['Salary_norm'] * 0.1
)

print(df[['Player', 'Overall Grade', 'Points Per Game', 'Rebounds Per Game', 'Assists Per Game', 'Salary ($M)']])
