# Introduction: 

    Air is one of the primary need for the living being and we are as a humans, breathe every minute of our life and that is why the quality of the air is crusial factor for the comfort and healthy living of each individual.

    In this project, we decided to work with a dataset containing reports on the weather and the level of pollution each hour for 5 years at the US Embassy in Beijing, China. 
    The level of pollution is represented by the concentration of PM2.5 which is airborne particulate matter. 

# What is PM2.5? 

    Airborne particulate matter (PM) is not a single pollutant, but rather is a mixture of many chemical species. It is a complex mixture of solids and aerosols composed of small droplets of liquid, dry solid fragments, and solid cores with liquid coatings.
    Particles vary widely in size, shape and chemical composition, and may contain inorganic ions, metallic compounds, elemental carbon, organic compounds, and compounds from the earth’s crust. 
    Particles are defined by their diameter for air quality regulatory purposes. Fine particulate matter is defined as particles that are 2.5 microns or less in diameter (PM2.5).

# Objectives: 

    Our goals:
  
        1. To find insights into the weather patterns and the possible reason for pollutation rates
    
        2. To develop a Deep Learning model that predicts pollution levels in the next hour
    
        3. To develop a Deep Learning model that predicts pollution levels the next day

#  Description:  

    1. Type of problem: regression.

    2. Variables: 11 Numerical, 1 Categorical:

          1. No: row number
  
          2. year: the year of data in this row
  
          3. month: the month of data in this row
  
          4. day: the day of data in this row
  
          5. hour: The hour of data in this row
  
          6. DEWP: Dew Point
  
          7. TEMP: Temperature
  
          8. PRES: Pressure
  
          9. cbwd: Combined wind direction
  
          10. IWS: Cumulative wind speed
  
          11. Is: Cumulated hours of snow

    3. Target: PM2.5 (float):
  
          1. pm2.5: PM2.5 concentration

    4. Steps we made

          1. Importing a dataset
  
          2. EDA
  
          3. Feature engineering
  
              1. Imputation of NAN values:
  
                    > KNNImputer
  
              2. Drop unnecessary variables
  
              3. Categorical variables encoding:
  
                    > CountFrequencyEncoder
  
              4. Scaling:
  
                    > Robust Scaler
  
              5. Train/test split:
  
                    > Train - 3 years
    
                    > Test - 2 years 
    
          4. Training ANN
  
          5. Model evaluation and result analysis

    5. Deep Learning Algorithms we used:

          > For predicting the pollution rate for the next hour:
  
                1. LSTM (Long-Short-Term Memory) with 2 hidden layers (100 neurons each).
    
                2. LSTM with 4 hidden layers (100 neurons each) + 3 Dropout layers (0.3)
  
          > For predicting the pollution rate for the next hour:
    
                1. LSTM (Long-Short-Term Memory) with 2 hidden layers (100 neurons each).

    6. Evaluation metrix we used:

          1. Mean Absolute Error (MAE)
  
          2. Mean Square Error (MSE)
  
          3. Root Mean Square Error (RMSE)
  
          4. R2 score

        
# Conclusion

##  Data Analysis

    After completing the data analysis step, we found several insights. 

          1. the imoprtant facotrs for dropping the air pollution is 
    
                1. Temperature
                2. Rain / snow
                3. Wind speed
         
  
          2. In 2010 and 2013 the pollution rates were the highest. 
          
                I suppose that dispite the fact that the rain, snow and wind rates were the highest during the 2010, the temperature was the lowest. and the government was not ready for that
                in Regard of 2013, the amount of Rain, Snow and Wind during that year was significantly low.
  
              
          3. During the first two years of the report, the most polluted season was Fall, While from 2012 to 2014, the most polluted season has changed to Winter.
  
         
          4. Summer was the least polluted season during all 5 years.
  
                It is because of the rain season in China and high temperature during that season.
  
         
          5. The most polluted months were usually February or January
  
          
          6. 2012 year was least polluted year, having the smallest mean pollution rate
  
                I suppose it is because the rain, snow, wind and temperature were relatively high during that year

            
        I suppose year by year the government tries to overcome the problem with air pollution.   

      
               
   ## Training & Evaluating ANN

        > For predicting the pollution rate for the next hour:

              1. The RNN model with 2 LSTM layers (100 neurons each) performs well showing the 91% r2 score at test set and 90% at train set without any sign of overfitting. 
  
                    It can be seen by the residual plot that the RNN model predicts well for the small as well as for the high values of Pollution rate with the minimum rate of error. 
  
                  
              2. The RNN model with 4 LSTM layers (100 neurons each) + 3 Dropout layers (0.3) performs well showing the 90% r2 score at test set and 88% at train set without any sign of overfitting. 
  
                    It can be seen by the residual plot that the RNN model predicts well for the small as well as for the high values of pollution rate with the minimum rate of error. 
  
                  
              3. It seems that the first model with 2 LSTM layers (100 neurons each) wors better in regard to both performance and the running time.

         
         > For predicting the pollution rate for the next day:

               I have trained the RNN model with 2 LSTM layers (100 neurons each) performs poorly showing only 35% of r2 score on train set and 36% on test set without any sign of overfitting. 
           
               It can be seen by the residual plot that the RNN model predicts poorly the high rates of pollution (>= 8000) Having huge residuals (>= 3000). However, it can also be seen that if the pollution rate is low (< 8000), the model predicts the pollution rate relatevely okay with relativelly low residuals (<= 1000).

                                

    I can conlude that its better to use Model with less LSTM layers to predict the Pollution rate for next hour due to the better performance, lower residuals and better training time.
    
    I suppose that predicting Pollution rate for the next day is still complicated task and more steps and techniques should be applied to boost the performance.
    
    However I think that the model is passible in predicting the low Pollution rate (<8000).

                

         
