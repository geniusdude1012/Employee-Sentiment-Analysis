# Employee-Sentiment-Analysis## Project Overview

This project analyzes employee sentiment through email communications to identify engagement levels, potential flight risks, and overall organizational sentiment trends.

## Key Findings

### Dataset Summary

- **Total Messages Analyzed**: {summary['dataset_summary']['total_messages']}
- **Unique Employees**: {summary['dataset_summary']['total_employees']}
- **Date Range**: {summary['dataset_summary']['date_range']}
- **Sentiment Distribution**: Positive: {summary['dataset_summary']['sentiment_distribution'].get('Positive', 0)}, Negative: {summary['dataset_summary']['sentiment_distribution'].get('Negative', 0)}, Neutral: {summary['dataset_summary']['sentiment_distribution'].get('Neutral', 0)}

### Top Performing Employees

"""

# Add top employees to README

if summary['top_employees']:
sample_month = list(summary['top_employees'].keys())[0]
readme_content += f"\n**Top 3 Positive Employees ({sample_month}):**\n"
for emp in summary['top_employees'][sample_month]['top_positive']:
readme_content += f"1. {emp['employee']} - Score: {emp['monthly_score']}\n"

    readme_content += f"\n**Top 3 Negative Employees ({sample_month}):**\n"
    for emp in summary['top_employees'][sample_month]['top_negative']:
        readme_content += f"1. {emp['employee']} - Score: {emp['monthly_score']}\n"

else:
readme_content += "\n*Insufficient data for employee rankings*\n"

# Add flight risks

readme_content += f"\n### Flight Risk Identification\nEmployees identified as potential flight risks (4+ negative messages in a month):\n"
for employee in summary['flight_risks']:
if employee != "None identified":
readme_content += f"- {employee}\n"
else:
readme_content += "- None identified\n"

# Add model performance if available

if len(X) > 5:
readme_content += f"""

### Model Performance

- **R-squared**: {r2:.3f}
- **Mean Squared Error**: {mse:.3f}
  """

readme_content += """

## Methodology

1. **Sentiment Analysis**: Used TextBlob for sentiment classification
2. **Score Calculation**: Monthly aggregation of sentiment scores
3. **Flight Risk**: Monthly negative message count (4+ negative messages)
4. **Predictive Modeling**: Linear regression for sentiment trend analysis

## Recommendations

1. **For Positive Employees**: Recognize and reward top performers to maintain high morale
2. **For Negative Employees**: Provide additional support and address concerns proactively
3. **For Flight Risks**: Conduct stay interviews and implement retention strategies
4. **Overall**: Monitor sentiment trends regularly and address systemic issues
   """

# Write README file

with open('README.md', 'w', encoding='utf-8') as f:
f.write(readme_content)

print("README.md file created successfully!")
print("All visualizations saved in 'visualizations/' folder")
