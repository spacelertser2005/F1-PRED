# Formula 1 Podium Prediction: A Data-Driven Approach

A machine learning project that predicts Formula 1 podium finishes using historical race data, qualifying performance, and driver statistics from the 2014-2024 seasons.

## Project Overview

This project analyzes 10 years of Formula 1 data to predict which drivers are most likely to finish on the podium (top 3 positions). Starting from a simple comparison of lap times between top teams and midfield teams, the analysis evolved into a predictive model that combines qualifying performance, sprint race results, pit stop efficiency, and historical driver performance.

### Motivation

Approached from the perspective of a Sports Analytics team working for a professional F1 team, this project aims to:
- Provide evidence-based insights for race strategy optimization
- Support data-informed driver recruitment decisions
- Enable pre-race probability assessments for strategic planning
- Understand what truly determines podium success in Formula 1

## Key Features

- **Predictive Modeling**: Logistic regression model with 84% ROC AUC accuracy
- **Multiple Data Sources**: Integrates qualifying times, sprint results, pit stops, and historical performance
- **Statistical Validation**: T-tests and regression analysis to confirm findings
- **Actionable Insights**: Probability estimates that support real-time race strategy

## Technologies Used

- **Python 3.x**
- **Pandas** - Data manipulation and analysis
- **Matplotlib** - Data visualization
- **SciPy** - Statistical testing
- **Statsmodels** - Logistic regression modeling
- **NumPy** - Numerical computations
- **Scikit-learn** - Model evaluation (ROC AUC)

## Dataset

**Source**: [Kaggle Formula 1 Dataset](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020)

**Data Includes**:
- Constructor standings
- Race results (2014-2024)
- Lap times
- Qualifying times (Q1, Q2, Q3)
- Sprint race results
- Pit stop data

**Key Variables**:
- `milliseconds` - Lap time for a single lap
- `team` - Constructor name
- `qualifying_position` - Driver's position in qualifying
- `sprint_result` - Finishing place in sprint race
- `pit_stop_time` - Pit stop efficiency
- `podium_finish` - Binary indicator (yes/no)
- `driver_podium_rate` - Historical podium success rate

## Project Structure

```
├── Formula_1_Project__Initial_Question_.ipynb    # Initial exploratory analysis
├── qualifying.ipynb                               # Qualifying data processing
├── qualifying_structured__Finalized_Question_.ipynb  # Final model and analysis
├── Matthew_Lertsmitivanta_Final_OBA465_F1.pdf    # Full project report
└── README.md                                      # This file
```

## Research Questions

### Initial Question
**"Do top-team drivers have significantly faster average lap times than other drivers across the last 10 seasons?"**

**Result**: Yes, with statistical significance (t = -5.870, p < 0.00001)

### Final Question (More Actionable)
**"Using qualifying times, sprint-race results and pit-stop efficiency, can each driver's probability of finishing on the podium be predicted?"**

**Result**: Yes, with 84% accuracy when including driver historical performance

## Key Findings

### Statistical Results

**Two-Sample t-Test**:
- t-statistic = -5.870
- p-value = 5.08 × 10⁻⁹
- **Conclusion**: Top-team drivers are significantly faster

**Baseline Model (Race-Day Data Only)**:
- Pseudo R² = 0.006
- ROC AUC = 0.547 (55%)
- Limited predictive value

**Full Model (With Historical Performance)**:
- Pseudo R² = 0.212
- ROC AUC = 0.841 (84%)
- Strong predictive capability

### Variable Importance

1. **Driver Podium Rate** (Historical): Most significant predictor by far
   - Coefficient: 6.98 (p < 0.001)
   - A 10% increase in historical podium rate dramatically increases podium probability
   
2. **Qualifying Time**: Moderately significant
   - Coefficient: -0.0078 (p = 0.004)
   - Each second slower reduces podium odds by ~0.7%
   
3. **Sprint Position**: Minimal effect when history is known
   - Coefficient: -0.0227 (p = 0.059)
   
4. **Pit Stop Duration**: Negligible impact
   - Coefficient: 0.0002 (p = 0.242)

### Predictive Example

**Driver A**: Q5, Sprint P6, 2.6s pit stop, 15% podium rate → **33% podium probability**

**Driver B**: Q5, Sprint P6, 2.6s pit stop, 40% podium rate → **72% podium probability**

*Same race-day performance, but historical success dominates the prediction.*

## How to Use This Model

### For Race Strategists

1. **Input Required Data**:
   - Best qualifying lap time (seconds)
   - Sprint race finishing position
   - Average pit stop duration
   - Driver's career podium rate

2. **When to Use**:
   - Pre-race strategy meetings
   - During qualifying to assess podium potential
   - For setting team expectations and priorities

3. **Outputs**:
   - Podium probability (0-100%) for each driver
   - Supports decisions on pit strategy, team orders, and resource allocation

### Running the Analysis

```python
# Install required packages
pip install pandas numpy matplotlib scipy statsmodels scikit-learn

# Run the main analysis notebook
jupyter notebook qualifying_structured__Finalized_Question_.ipynb
```

## Visualizations

The project includes several key visualizations:

1. **Top Teams Identification**: Bar charts showing championships and race wins
2. **Qualifying Time Distribution**: Before/after outlier removal (cleaned to 75-100s range)
3. **ROC Curves**: Comparing baseline (55% AUC) vs full model (84% AUC)
4. **Analytics Flowchart**: Complete methodology from data access to stakeholder communication

## Insights for Team Strategy

1. **Driver Selection**: When choosing between similarly performing drivers, prioritize those with stronger podium track records

2. **Pre-Race Briefings**: Use model predictions to align team expectations and allocate support

3. **Strategic Risk**: Consider podium history when assigning team orders or riskier pit strategies—data shows it matters more than sprint finish alone

4. **Qualifying Focus**: While history dominates, qualifying performance still matters significantly

## Future Extensions

Potential improvements and expansions:

- **Weather Conditions**: Integrate wet/dry race conditions
- **Tire Strategy**: Include tire compound choices and degradation
- **Real-Time Updates**: Incorporate live race variables (safety cars, position changes)
- **Full Race Position**: Extend beyond podium to predict finishing positions 1-20
- **Season-Long Performance**: Multi-race predictions for championship modeling
- **Circuit-Specific Models**: Adjust for track characteristics

## Top Teams Analyzed

Based on championships and race wins (2014-2024):
- **Ferrari**
- **McLaren**
- **Mercedes**
- **Red Bull Racing**

## License

This project was created for academic purposes (OBA 465 course).

## Author

**Matthew Lertsmitivanta**

Project completed: May 14, 2025

## Acknowledgments

- Kaggle for providing the comprehensive Formula 1 dataset
- OBA 465 course instructors
- Formula 1 community for domain expertise

---

*For detailed methodology, statistical analysis, and complete results, please refer to the [full project report](Matthew_Lertsmitivanta_Final_OBA465_F1.pdf).*
