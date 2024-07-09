# 100 Days Verification Challenge - Day 28 - STA numerical

## 1. Given the following flip-flop circuit with a delay dly between input and output. And the clock CLK is applied to the flip flop.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/0e3b1dd9-07eb-4555-9152-2d5c5dc8b2da)

## a. What will be the expression for the minimum time period (Tminimum) or maximum clock frequency (fmaximum)? Derive it by considering clock to Q delay (Tclock_Q), setup time (Tsetup_time), and hold time (Thold_time) of the flipflop.
## b. If the value of dly = 0ns, and given three flipflop values as per the table below, Which of the flip flops are a good fit when the minimum required time period is 5ns, 8ns, and 15ns.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/7a4cbbb5-85fa-4aae-a529-55e5d9518735)

### Solution:

a. From the above-given circuit

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/24ad3a0a-2cd5-44ba-b02d-1a38647e7ab9)

1. The output Q will be changed only after the clock event and till the clock to Q delay elapsed.
2. Also the input data has an external delay of dly will add up to Tclock_Q
So the expression will be for minimum clock period will be as below,
Tminimum >= Tsetup_time + Tclock_Q + dly

b. By using the above Tminimum expression let us calculate the minimum time periods for flip flops FF1, FF2, and FF3 respectively.

Tminimum for FF1 = Tsetup_time of FF1 + Tclock_Q of FF1 + dly
Tminimum for FF1 = 3ns + 5ns + 0ns
Tminimum for FF1 = 8ns

Tminimum for FF2 = Tsetup_time of FF2 + Tclock_Q of FF2 + dly
Tminimum for FF2 = 6ns + 4ns + 0ns
Tminimum for FF2 = 10ns

Tminimum for FF3 = Tsetup_time of FF3 + Tclock_Q of FF3 + dly
Tminimum for FF3 = 8ns + 2ns + 0ns
Tminimum for FF3 = 10ns

For the time period requirement of 5ns none of the above flops can be used, and for 8ns flop FF1 alone can be used. Whereas for the time period requirement of 15ns any one of the above flip flops can be used.

## 2. Given the data setup time of the flop is 6ns, the hold time of the flop is 2ns, and the clock to Q delay is given as 10ns.
## a. Calculate the minimum clock period required to handle the circuit by drawing a digital logic circuit for function clock frequency divided by 2.
## b. Also determine the status of hold time violation and give a proper reason.

### Solution:

a. The logic diagram for clock frequency divided by 2 would be as shown below.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/8290b466-fed5-4b7a-a688-ab2453655339)

The waveform of fin and fin/2 are as shown below

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/8507387a-2986-48bf-bba5-f6e234eefed1)

By using above discussed Tminimum expression let us calculate the minimum time period,

Tminimum >= Tsetup_time + Tclock_Q + dly
Tminimum >= 6ns + 10ns + 0
Tminimum >= 16ns

fmaximum >= 1/16ns
fmaximum >= 62.5MHz is the maximum possible frequency of operation for an above circuit with given timing requirements.

b. Let us check for the hold violation, we have the hold time constraint as discussed at the starting of this article,
Thold_time <= Tclock_Q + delay
2ns <= 10ns + 0
2ns <= 10ns
As we are satisfying the above condition there is no hold time violation in the circuit as per the given timing requirements.

