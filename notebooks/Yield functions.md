Yield functions

1. 1 dimensional rain  
    assumptions: 
        madhya pradesh soybeans
        sowing: early-mid june. 
        growing periods: june july august 
        TECHNICALLY, sowing happens with the onset of the monsoon, which changes year to year and even region to region
        basically, there needs to be intial soil moisture (AND THEN CONTINUED SOIL MOISTURE) for sowing to occur
        so monsoon has to start and then we start sowing basically. 
        officially, the monsoon season is june 1 to september 30th (june july august september, so about 120 days. if you plant at around june 15, then september 30th marks the end of about 105 days)
        harvest: september october (november)
        assumptions from rajesh kumar et al 2002 meterology paper 


        OK how about for testing purposes, let's just say: june is the sowing, halve the june data + july + august + september (gives 105 days). october is the harvest month
    1. sum of growing period rain <= 800 mm
        a. flat threshold payout 
        b. linear threshold payout 
        c. linear threshold, with two different coefficients at 800 and at 65 
        d. quadratic function, peak at 800, goes down. 
        c. absolute value reversed but peak at 800 (inverted triangle)
    2. any month in harvest period rain >= 30 mm (ie. the one month harvest period)
        a. flat penalty if the harvest rain >= 30 mm
        b. linear penalty 
2. 2d rain temp
    assumptions:
        same as 1 d rain
    1. 1d rain niceties
    2. temp also needs to be below 35 C 
        a. flat penalty
        b. linear penalty 

3. need to bake in some variability into the simulator (ie. the yield function predicts this, the actual is yield + N(0, gamma), where we input some constant coefficient of variation)
    WE SHOULD FIND THE AVERAGE YIELD PREDICTED BY THE FUNCTION OVER THE REAL RAIN DATA. THEN, MATCH THAT TO ACTUAL YIELD DATA (ie. the actual yield mean) AS BEST AS WE CAN. THEN, TAKE THAT MEAN TO various coefficient of variations

    