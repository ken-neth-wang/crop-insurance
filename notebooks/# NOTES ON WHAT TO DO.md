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