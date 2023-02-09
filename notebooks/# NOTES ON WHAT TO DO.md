# NOTES ON WHAT TO DO 


1. break up into monthly rain (more granualr vector), maybe try add more months in the beginnings, total, monthly, cumulative (infer things from weights), regress on each, just try to remove variables / preven overfitting them
wed feb 8: done this, don't have enough good data to make a good yield function tbh, 0.3 R2 


2. add variables (growing degree days into the function): growing degree days (find base temperature, which is 54 for soybeans), humidity 
wed feb 8: haven't done this,not enough yield points to include 

3. make sure low troughs are good 
feb 8: checked using plot_summary_trials, makes sense from what I know

4. add in insurance policies (ie. work on )
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
5. 




Things I would like to do: 
1. make code more readable
2. Create Simulation Class, and then vary the insurance policy in each class (so then the code is standardized, basically Object Oriented Programming)