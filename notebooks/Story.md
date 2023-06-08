Story:
# data
rain data is pulled from 117 years of meterological data surrounding the Eastern Madhya Pradesh region in India, which accounts for 58% of Indian soybean production. 

Based on agricultural research papers, the rain data was summarized into two variables:

1. Growing rain (which corresponds to rain during the growing season) was calculated through taking half of June rain and adding to July, August, and September rains. 

    This represents a typical growing season where the sowing begins in early June, however there may be more variability since weather conditions and prediction of monsoon rains may spur farmers to sow earlier or later. 

2. Harvest rain (rain during the harvest period) was calculated through taking October's rain, since harvest period takes about 1 month. 

    Again, similar to growing rain, this exact number may be more variable since farmers may choose to delay their sowing peirod due to delays in monsoon arrival. 


Growing Rain mean and standard deviation:  
Mean: 1004.9 mm
Standard Deviation: 39.4 mm

Figure 1. Growing Rain Histogram


Rain to Yield

Initially, attempted to find function mapping rain to yield for soybeans in a given region (ie. Eastern Madhya Pradesh). However, lack of sufficient yield data for a specific region made this approach not very good. 

Thus, rather than utilize a rain to yield function that isn't very good, this model generalizes findings from research papers analyzing soybean yield based on rain data. The function assumes yield linearly increases as rain increases until about 800 rain, where the yield begins to taper off negatively slightly. 

For insurance purposes, the insurance payout predicts the expected yield (which is the actual yield in this simulation) and adds a noise value. This noise is an iid Normal with mean of 0 and a standard deviation between 50 and 300 (yields over the empirical rain data has a mean of 1098.7 and a sample standard deviation of 29.42, so this range of predictor standard deviations seems reasonable). 

Increasing this standard deviation essentially corresponds to increasing variations in yield due to a wide range of factors. For instance,this could simply be yield variance due to external factors such as pests, disease, or other weather factors that could increase or decrease yields, or it could be internal factors such as variance in the yield prediction models used by the insurance providers or imprecision in the weather data measures in the local regions. 

Figure 2. Rain to Yield Function

Yield to Cash 

The yield to cash function was developed based on numbers from a marketing study. However, this function is very much a general estimate, since actual cash revenues and costs of production will vary from farmer to farmer. In general, this function is simply a linear transformation, where farmers will make more revenue from higher yields and have a fixed cost of production. The breakeven point (in terms of rain) occurs around 650 mm of rain (in other words, farmers will make a profit if the growing rain is above 650 mm)

Figure 3. Rain to Yield Linear Function 




# assumptions

Insurance Policy

Mirror: Insurance policies are written to be the mirror of the predicted cash that farmers will make given a certain rain amount. Thus, if the predicted cash yield is a quadratic function, the insurance policy will be the negative of this quadratic.  
Non-negative payouts: Insurance policies are also assumed to charge a flat premium, and then payout a given value for certain thresholds. This payout is assumed to be non-negative.

Thus, insurance policies payouts = max(- predicted_yield, 0). 

predicted_yield = actual_yield + N(0, std_dev_param)

Cash to Farmers with and without policy

Cash to farmers without policy = yield_to_cash(actual_yield(rain)) 
                               = rev * actual_yield - fixed costs 
                               = rev * (predicted_yield + N(0, std_dev_param)) - fixed costs


Cash to farmers w/ policy = yield_to_cash(actual_yield(rain)) + insurance_payout - premium 
                          = yield_to_cash(actual_yield(rain)) + max(- yield_to_cash(predicted_yield), 0) - premium


Insurance Premiums

Insurance premiums are calculated through Monte Carlo simulation by finding premium value such that the insurance policy has expected value of 0 over the empirical rain data.  

Figure 4. insurance payout over range for absrain



# ablation study 

-> tweak variables
