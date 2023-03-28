# NOTES ON WHAT TO DO 


1. break up into monthly rain (more granualr vector), maybe try add more months in the beginnings, total, monthly, cumulative (infer things from weights), regress on each, just try to remove variables / preven overfitting them
wed feb 8: done this, don't have enough good data to make a good yield function tbh, 0.3 R2 


2. add variables (growing degree days into the function): growing degree days (find base temperature, which is 54 for soybeans), humidity 
wed feb 8: haven't done this,not enough yield points to include 

3. make sure low troughs are good 
feb 8: checked using plot_summary_trials, makes sense from what I know

4. add in insurance policies (ie. work on)
    a. determine insurance policy payout, premium, and expected value for insurance company (has to >= 0)
insurance policies, you just buy x amount of insurance 
        i. do this by empirically calculating expected value through monte carlo simulations (just as for the farmer) the payout vs payments
    b. determine thresholds / functions of the insurance policies and test them 
    c. vary over starting cash and insurance amount being bought


feb 8 meeting notes: 
1. rain in soil moisture -> leads 
2. understand what times of year does the rainfall matter -> maybe read this from the papers
3. irrigation -> look into it more 
4. main issue: developed world has differenet mindset -> auto insurance premium vs crop insurance
5. also farmer behavioral -> willlingness to buy insurance (what makes them buy)


next steps: 
1. start with double threshold, double payout, while holding expected payout 
2. hold expected payouts = 0, change the thresholds and play around 
3. rain->insurance_payout: compensate for average reduction in yield

1. vary over cash and insurance
2. one extreme is cash poor, contrasinted by cash and can't buy as much insurance as eoptimal 
3. other extreme is assume unconstrained 

assume unconstrained

demonstrate that
1. adding second weather factor improves yield (duh)
2. adding second weather factor is feasible for insurance 
3. show that double threshold is better than single threshold
    time to bankruptcy
    utility function calculate the expected utility 
    shortfall from assumed threshold on income, expected shortfall 
    cash after 5 years from some x assumed cash (distribution) 
4. show that annual rainfall is not useful as opposed to monthly 


Things I would like to do: 
1. make code more readable
    A bit more readable (everything after the data and pre-processing)
2. Create Simulation Class, and then vary the insurance policy in each class (so then the code is standardized, basically Object Oriented Programming)
    monday feb 20 update: I basically did this but with a general insurance_sim function, then we pass everything into the function based on what we want


feb 20 work: 
1. fixed code a bit to be more readable
2. created a better plot summarizer 
    a. plotting each trial's cash with and without insurance 
    b. summarizing over all the trials what happens to the farmers
3. use monte carlo to determine values for each type of insurance policy each parameter, parameters: premium, payout, threshold value(s) -> hold others, change one
    a. check that over all the trials that the percentage payouts 
    b. ok, instead, coded a thing taht determines the premium for payout and threshold value that sets expected value = 0 


4. summary of what my insurance functions do: 
    a. I first set-up a plotter
    b. then, i set-up a monte carlo simulation that determines how often a certain policy will payout (given certain threshold values)
    c. then, I set-up a function that determines for a fixed payout (since payouts can be adjusted using amount of insurance purchased) 
    what the appropriate premium would be for that threshold value (and payout percentage)
    d. finally, i have the payout, the premium, and the threshold values that reuslt in expected value of 0 for the insurance company 
    e. i then iterate over possible amounts of insurance the farmer can buy to test the difference


1. try different amounts of insurance

STILL NEED TO DO: 
2. try to set-up different types of insurance
3. try to set-up different metrics to measure: 
    a. time to bankruptcy 
    b. some utility function 
    c. shortfall from assumed threshold on income, expected shortfall
    d. cash after 5 years from some x assumed cash 




OTHER THINGS: 
1. maybe design the insurance simulator to automatically find the EV neutral payout amount (ie. each simulation, the insurance company comes out at EV = 0)


feb 20 questions: 
1. given that my yield function is linear, does it make sense to have a double threshold? 
    to answer my own question, maybe I can set thresholds based on the different months 

feb 20 FINDINGS: 
1. using single-lower-threshold policy, simulations show that for low binary thresholds (less than 10% of payout probability), the farmers are actually hurt even more in down years ON AVERAGE 
    a. we can see this from looking at graphs for year 2, where year 2 is on average a down year (lowest cash from yields without insurance). In this case, with low payout probabilities, farmers are better off on average without the insurance, simply because they are paying a bit of many but then not actually getting the stabilizing effect due to low probability of payout. 
2. as expected, increasing the amount of insurance (ie. the # of contracts purchased) increases the deviations, with everything else hold constant
3. 


feb 20: next steps
1. just use 10 trials, look at 10 farmers and go through rain, yields, to show that each farmer works (examples) 
    figure out what's going on with low troughs 
    find explanations 
2. try quadratic (eyeball the function and just make it up lowkey) function 
    -> then use a double threshold 
3. explaining why certain things happen (ie. the low troughs in the single-lower-threshold-policy)



march 8 steps: 
1. let's try 10 trials (ie. 10 farmers).
    plotting the insurance payments, it's clear that the policy is paying out when it really shouldn't be. That's causing bad performance. 
    IDEA: we should be constructing an insurance policy that 1. pays out more often (like 50% of the time), 2. 
    ok even on linear, the problem is that the rain and yield predictor is still not good enough (too many times where the rain and the yield don't actually line up well)
    in such cases, the bad cases can get amplified more than they should be
March 9 notes: 
1. From plotting specific farmers, I've realized that my yield to rain is not very good. In other words, making new yield to rain that is a bit better. 
    OK SO I tried to do PCA so I can build a quadratic function / simplified function. 


    at planting time, we know the past 6 months of weather. so we should be only considering the next 6 months of rain. 



    ok so now, we have a lin_reg_india function that predicts based off the last 6 months. Then, x[7] and x[11] are actually negative and not good. 

should i just simplify the rain to yield function? right now its based off 12 months, but PCA will make it unintelligible



may june july, planting, august, growing, septmeber october harvest

take a look at the data to see if these relationships actually exist 


1. try to get more data 
2. look at the last couple of years of data 



march 22 notes 
1. going to assume jun/ jul is plant, august is grow, sept/oct is harvest 
2. paper I'm looking at looks at soybean yield responses to precipitation and temp
    a. they are saying negative relationship on maximum temperature from 24 to 29 degrees c
    b. roughly quadratic looking (inverted U) curve for the response to precipitation
    c. this paper is using max and min temperatures
3. robertschlenke -> temp increases until 29 c, then goes down 
4. online says jun jul plant, august, sept oct harvest
5. precipitation matters, especially during growing season -> increased yields
        https://www.ars.usda.gov/ARSUserFiles/3495/soybean%20CC%20AJ%202021.pdf
        On the other hand, Mall, Lal, Bahatia, Rathore, and
        Singh (2004) predicted that CROPGRO soybean yield would
        decrease in India at elevated air temperature and doubled CO2
        concentration. 
6. soybean planting date is critical 
    https://www.sciencedirect.com/science/article/pii/S0168192303001576?via%3Dihub
7. https://rmets.onlinelibrary.wiley.com/doi/pdf/10.1017/S1350482702002104
    specifically, >= 80 cm of water during growing period, (first 100 days), then last 15 days should be dry (<= 3 cm)
    temperature <= 36 (specifically in madhya pradesh)
    5cm or more received before sowing
8. indiaagronet
    15 -32 c, higher temp for rapid growth
    60-65 cm  rainfall at or just before flowering
    rains during maturity hurts quality of yield
    https://www.agrifarming.in/soybean-farming-information
    26-32 c
    soybeans: short day plants
    https://www.nsdcindia.org/scmp/assets/image/1913597640-20_SoybeanProductionTechnology_preview.pdf
    resistant to temperatures, decrease above 35 c, and below 18c 
    minimum temperatures if 10c
    26 - 30 c is optimum temperatures for growth
    40-50 cm in season-> high moisture for germination, flowering, and pod formation
    180 mm is minimum for in-crop rain, 40-60% yield decline, ideal is 500 - 1000 mm
    5-15 days of drought can also result in death of crop 
    growing period is 100 to 130 days 
    stages: vegetative growth -> reproductive
    cycles: sow -> germination (5 days or so after sowing) -> emergence -> flowering -> pod formation -> maturity of pods

OH WAIT 
ok I have data from multiple regions rainfall for the last 10 years. I probably can also find the yields for those regions for the last 10 years. maybe I can use that? -> try to build off of that data 

OR i can boot camp / use windows desktop back at home, and try running the CROP gro simulation to get a yield model and vary rainfall amounts 

if i were to guess, we should follow the kumar paper on optimal sowing dates from 2002
1. week before sow: >= 50 mm of rain
2. crop growth (~100 days after sowing): >= 80 mm of rain
    excessive flooding is bad, so flooding for more than 48 hours is bad -> not sure if we can control for this in anyway, since we are looking at monthly 
        -> maybe there's a variable of like if there's sustained flooding for more than 48 hours, triggers a payout
    https://extension.umn.edu/growing-soybean/flooded-soybean#temperature-during-the-flood-542761
    https://www.canr.msu.edu/news/how-does-flooding-affect-soybean-germination
3. harvest period (15 days, after crop growth): <= 30 mm of rain
4. temperature: max temperature <= 36 C in a week during growing
        we can also probably add that min tempearture >= 15 during growing 


https://www.ukm.my/ipi/wp-content/uploads/2013/07/57.1999Growth-and-yield-responses-of-soybean-in-Madhya-Pradesh.pdf
1. USED CROP GRO to simulate soybean responses to temperature and rainfall (in c02, for climate change predictions)
    -> % increases in cumulative rainfall would respond with increased changes in yields
    -> -4 to 0 change in temperature would result in inc in yields, while increases would result in worse and worse yields 
        -> THESE OUTCOMES MATCH THE RESULTS FROM OTHER PAPERS ON SOYBEAN AND RESPONSES TO CLIMATE CHANGE

burning degree days + growing degree days (penalize for burning) 
variables:
1. rain in growing
2. rain in harvest
3. burning degree days
4. growing degree days 
build predictive model based off this 

main goal: 1. show that single threshold is worse than alterantives,    
2. assumption is that rain is good up to a certain point, harvest rain is bad, burning degree days 
    say that there's some degree of variability (expected yield - actual yield)
        play around with what that variability will be (vary over some degree of variability)
        might discover that certain policies is bad for the farmer even if you can predict the yield with accuracy 

3. play around with percentiles 
4. figure out -> is variability ends up the same for hte farmer's income



1. what is shape of the yield? 
2. variability -> think about hte standard deviation and the coefficient of variation for the built 

march 27: from last meeting, going to ignore the whole data / building yield model for now: 
1. remedy by saying that we have some yield function, with x level of variability. this yield function has some very basic understanding of the general relationship between temperature / rainfall and the yields
2. for instance, yield function is a inverted triangle. in the good region, the yield function has good variability but in the bad region, the coefficient of variation is much higher 


* Next Steps * 
1. code up yield function class 
2. code up insurance policy class 
3. code up simulator (modify current code)


