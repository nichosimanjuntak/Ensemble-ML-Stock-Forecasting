# Ensembled Machine Learning Method for Stock Forecasting
*A machine learning project under the IEDA3330: Introduction to Financial Engineering course*

This project applies three machine learning models—Random Forest, Gradient Boosting, and Neural Networks—to predict stock prices for two contrasting companies:
- Johnson & Johnson (JNJ): A stable blue-chip stock
- Microsoft (MSFT): A growing big-tech stock <br>
The goal is to compare model performance, evaluate predictive accuracy, and explore how well each model captures different market behaviors.

## Models Implemented
1. Random Forest
   - Key Features: Ensemble of decision trees, bootstrapping, feature bagging
   - Strenghts: Reduces overfitting, handles non-linearity, shows features importance
   - Weaknesses: May underfit if important features are missed
2. Gradient Boosting
   - Key Features: Sequential error correction, learning rate tuning
   - Strenghts: High accuracy, good with complex patterns
   - Weaknesses: Prone to overfitting
3. Neural Network
   - Key Features: Multi-layer perceptron with ReLU activation, L2 regularization
   - Strenghts: Captures non-linear relationships, adaptable
   - Weaknesses: Computationally intensive, requires tuning

## Data and Features
1. Data Sources: Yahoo Finance via yfinance library
2. Features Created:
   - 'Close_Yesterday': Close price yesterday
   - 'High_Yesterday': Highest price yesterday
   - 'Low_Yesterday': Lowest price yesterday
   - 'Open_Yesterday': Open price yesterday
   - 'Volume_Yesterday': Amount of volume yesterday
   - 'High_Low_Range': Range of highest and lowest price yesterday
   - 'MA5_Weekly': Moving average of 5-days close price
   - 'MA21_Monthly': Moving average of 21-days close price
   - 'Vol_W_MA5': Moving average on the 5-days amount of volume
   - 'Vol_M_MA21': Moving average on the 21-days amount of volume
   - 'C_EMA5_Weekly': Exponential Moving Average for 5-days close price
   - 'C_EMA21_Monthly': Exponential Moving Average for 21-days close price
   - 'Vol_W_EMA5': Exponential Moving Average on the 5-days amount of volume
   - 'Vol_W_EMA21': Exponential Moving Average on the 21-days amount of volume
3. Preprocessing: z-score normalization for neural networks

## Results Summary
Error Calculation using MAPE:
1. Random Forest
   - JNJ: 0.7%
   - MFST: 1.2%
2. Gradient Boost
   - JNJ: 0.7%
   - MFST: 1.1%
3. Neural Networks
   - JNJ: 0.6%
   - MFST: 1.3%

#### Ensemble Model
A weighted ensemble of the three models was built, with weights based on validation errors:
- JNJ: RF (0.338), GB (0.362), NN (0.300)
- MSFT: RF (0.296), GB (0.282), NN (0.422)

The ensemble smooths individual model weaknesses and provides balanced predictions for both stable and volatile stocks. <br>

Error Calculation using MAPE:
- JNJ: 0.7%
- MFST: 1.7%

## Key Findings
1. All models perform well on JNJ (stable stock) with MAPE < 1%.
2. MSFT (volatile tech stock) is harder to predict, especially during sharp price changes that assumed to be because of market news (sentiment) that the model does not directly taking into account.
3. Neural networks capture volatility better but are prone to overfitting.
4. The ensemble model offers the best trade-off between stability and adaptability.

## Further Recommendation
1. Incorporate news sentiment and macroeconomic indicators
2. Experiment with LSTMs or Transformers for time-series modeling
3. Engineered more features with wider timespan to better forecast volatility
