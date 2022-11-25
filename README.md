# Credit Contingent Interest Rate Swap Valuation


A credit contingent interest rate swap is an option that grants its holder the right, but not the obligation, to enter into an interest rate swap (IRS) at the time when its reference obligor defaults. The premium to be paid on the underlying IRS is fixed in advance at some strike level. The notional amount of the swap is a function of a predetermined fixed amount and the recovery rate of the reference obligor. The model can also be employed to back out an implied correlation between the interest rate and the default arrival of an obligor.

The valuation model is a simplified closed form solution, in which a lognormal process for the swap rate and an Ornstein-Uhlenbeck (OU) process for the hazard rate are assumed.  Both processes are one-factor models and they couple to each other in a standard way. The volatility skews and smiles for swap rates are calculated via a stochastic volatility model, namely SABR model. The default probability of the reference obligor is calibrated to the credit default swap (CDS) market and the volatility of the hazard rate is implied by the market information of CDS options (CDSO).  

The correlation between the swap rate and the hazard rate of an obligor is not a market observable and should be implied from the CCIRS market. For an obligor whose market implied correlation information can not be found, a historical analysis has to be used to obtain a reasonable estimate and a pertinent reserve has to be set up. A reserve methodology has been proposed by GRMMR London to address parameter uncertainties and approximations in the model. 

The credit contingent interest rate swap (CCIRS or CCDS) valuation model serves the purpose of pricing an option that grants its holder the right, but not the obligation, to enter into an interest rate swap (IRS) at the time when its reference obligor defaults. The premium to be paid on the underlying IRS is fixed in advance at some strike level. The notional amount of the swap is dependent on a predetermined fixed amount and the recovery rate of the reference obligor.  

In essence, a CCIRS trade can be regarded as an interest rate swaption with two special features. One is that the maturity of the swaption is the default time of the reference obligor, which is unknown. The other feature is that, although the strike of the underlying swap is predetermined, the tenor and the notional amount of the underlying swap are dependent on the default time and recovery rate of the reference obligor, respectively. The trade provides a hedging of the counterparty risk in an IRS. 

The pricing and risk management of CCIRS trades depends on correlation between the default arrival of the reference obligor and the market value of the underlying IRS. For this reason, it is necessary to model the correlation, which can only be achieved by modeling the dynamics of the interest rate and the credit.  The dynamic model of interest rates has been well established. Following the same methodology as that of interest rate modeling, people have also tried to model the default arrival via dynamics of either credit spreads or hazard rates. There have been several attempts to model the correlation between interest rates and credit. 

The model is a simplified closed form solution, in which the swap rate dynamics are modeled as a lognormal process and the hazard rate dynamics are modeled as an Ornstein-Uhlenbeck (OU) process. Both processes are one-factor model and they couple to each other in a standard fashion. Although the model is simple compared with other proposed models, the apparent advantage of the model is that the basic instruments in a CCIRS trade, namely the swaption and the CDS, can be priced correctly. The effect of correlation between interest rates and credit can be explicitly quantified with known reasonable approximations.

Like all interest rate dynamic modeling approaches, the CCIRS model involves many parameters which should be calibrated to the pertinent market information. In the pricing of an interest rate swaption Black volatilities are calculated via a stochastic volatility model (SABR model), which is an approved model for the volatility skews and smiles. The default probability of the reference obligor is calibrated to the credit default swap (CDS) market and the volatility of the hazard rate is implied by the market information of the CDS option (CDSO).   

The Correlation between interest rates and hazard rates can only be observed from the market information of the CCIRS itself. Therefore, apart from pricing, the model can be employed to back out the implied correlation.  For an obligor whose market implied correlation information can not be found, a historical analysis has to be used to find a reasonable estimate and a pertinent reserve has to be set up. A procedure for determining a reserve has also been proposed by GRMMR London to address the uncertainties of the parameters and the approximations in the model. 

The risk computation of the CCIRS trade has also been implemented in the submitted model. There are risk measures related to the interest rate, which are defined and calculated in the same way as those for swaptions. Only the credit related sensitivities are tested. Specifically, these are the credit spread sensitivity, the default sensitivity, and the correlation sensitivity. 

Consider a CCIRS trade with a notional amount , a maturity T, a strike K for the underlying swap, and a reference obligor. The reference obligor is described by a credit spread curve , a recovery rate , and a default time .  

When the reference obligor defaults before T, the pay off function of the trade can be written as:

(1)	 ,

where   is the forward swap rate starting from   to the CCIRS maturity  .   is the annuity of the fee leg for the swap.   takes the value +1(-1) for the underlying swap where the option holder pays (receives) a fixed premium. For simplicity we assume  hereafter. 

The present value (PV) of the CCIRS trade at the valuation time (time zero) then reads:

(2)	 

  is the price of a default free zero coupon bond (see https://finpricing.com/lib/FiBondCoupon.html) with maturity  . The definition can be expressed as:

(3)	 ,

where we assume the default-free continuously compounded short rate   to discount the final payoff of 1. 

For the reference obligor, a hazard rate, , is defined such that the default probability between s and s+ds is  . The unconditional survival probability of the reference obligor reads:

(4)	 .

In this model, the interest rate dynamics are modeled as a lognormal process for the swap rate. It has been well known that, under the annuity measure, the forward start swap rate is a martingale and follows a zero drift lognormal process, shown as:

(5)	 ,

 where   is the volatility and  is the standard normal random driving force of dynamics. 

The dynamics of the hazard rate for the reference obligor are modeled as an OU process:

(6)	 ,

where   is the mean reversion rate and   is the mean reversion level.
 
We assume the swap rate and the hazard rate are correlated, i.e.,

(7)	 

holds for some correlation parameter  . Note that this is the standard way of coupling two stochastic processes.

The analytical solutions exist for both the swap rate dynamics and the hazard rate dynamics:

(8)	 

  is the forward swap rate starting from t to T seen at time zero.     is assumed constant hereafter. 

As indicated in Eq. (4), the survival probability always involves the integral of the hazard rate. Therefore, it’s useful to define another variable . It is well known that   is normal with mean and variance given by:

(9)	 

 where 

(10)	 .

The unconditional survival probability of the reference obligor seen at time zero can be expressed as:

(11)	 .

 is the hazard rate term structure seen at time zero, which can be calibrated by the credit spreads and the recovery rate observed at time zero. The details of calculating  can be found.

Starting directly from the pay off function Eq.(2), we can analytically solve the CCIRS pricing model using the following procedure:

i.	We discretise the time axis into n points  with a constant interval and the PV of the CCIRS trade can be rewritten as:

(12)	 .

ii.	In order to calculate , we work under the annuity measure . Note that Eq. (12) is under the normal risk neutral measure while Eq.(5) is true under the annuity measure. Following a standard way of changing measure, we have

(13)	 .

iii.	 The expectation can be solved under the annuity measure:

(14)	 ,

where   is the standard bi-variate normal distribution function, known as:

(15)	 .

After lengthy deductions, the expected value can be found to have the form:

(16)	 ,

 where

(17)	 .

 is the standard cumulative normal distribution function.

iv.	Putting all of them together, we can explicitly write the value of the CCIRS as

(18)	 
with

(19)	 

and
(20) 	 

We need to work out , which is defined as the correlation between   and . We calculate the covariance between them 

(21)	 

If the correlation between the interest rate and the hazard rate is assumed to zero, Eq. (18) can be simplified as

(22)	 .

It can be seen from Eq. (22) that the CCIRS can be regarded as a portfolio of swaptions weighted with the default probabilities. This scenario serves as a very important role in the pricing. Eq. (22) suggests that the CCIRS value can be inferred directly from swaption price and the single name CDS price, both of which have very liquid markets. The value of the CCIRS trade actually can be priced exactly and all the assumptions of the dynamics become irrelevant. 

The approximations and their possible implications can be summarized as follow:

•	Discretization as shown in Eq. (12) is an approximation. The discretization interval has to be reasonably small. However, too small time step will consume too much computation time. In the model the discretization interval is an input parameter, which can be chosen at user’s own discretion. A criterion of choosing this discretization interval has to be set up with both the precision and computational efficiency taken into account. As shown in the next section, a weekly discretization interval is small enough and can be reasonably relaxed to a larger one. A discretization interval  is acceptable, if the following equation is met:

(23)	 .

Eq.(23) essentially means that, even if we tighten the interval to one week, the change of the value is within one basis point, which is not material in term of pricing a trade.
 
•	The swaption value as shown in Eq. (18) is calculated using a standard Felix function available in the system. However, when the strike of the underlying swap changes due to the effect of correlation, the function automatically looks for an implied volatility supplied by the SABR model. Normally this implied volatility will be different from the original volatility used to calculate , although it is expected that the caused inconsistency should be small. In order to assess the difference, a valuation consistency check has been implemented in the model in which the original volatility is employed. As shown in the next section, the discrepancy is small if the correlation is small. The model should only be used if the discrepancy between the value of the trade and the consistency check value falls within one basis point, shown as:

  (24)	 


•	The assumption of an OU process for the hazard rate can give us certain probabilities of negative hazard rates. A negative hazard rate assumes a larger than one survival probability of an obligor hence is incorrect. Because the OU process is calibrated to the hazard rate term structure which is always positive (shown in Eq. (11)), there is no implication of this feature for linear payoff functions. However, if the payoff function is nonlinear like the case of the CCIRS trade, it may have implications.  This maybe one of the reasons that a negative CCIRS value is observed when the correlation is close to either 1 or -1.

•	The interest rate dynamics are simplified by assuming a one factor model. It is well known that the existence of volatility skews and smiles makes interest rate derivative modeling very complicated.  In the model, volatilities skews and smiles are captured by simply supplying different Black volatilities to Eq. (18), not Eq. (5). A “theoretically” proper way should be putting different volatilities in Eq. (5).  However, if we do that, the modeling falls into the general modeling framework of the BGM model (for information on this topic see, for example). It is almost impossible to solve such problem using the current methodology. In the CCIRS model, the problem is reduced so that we are only concerned with a single swap rate at each period. We are not concerned with the covariance between different swap rates, which can be considered as a high order effect as far as the pricing of a CCIRS trade is concerned. A one factor swap rate model is in fact sufficient for this purpose and consistent with the accepted standard approach for pricing vanilla contracts on a single rate such as swaptions. Moreover, the correlation between the interest rate and the credit comes is calibrated by the market information of the CCIRS trade using Eq. (18). Possible high order effects can be absorbed in this parameter.

•	As far as we know, at the present time the CDS option market is not complete and/or liquid enough such that a volatility skew and simile structure can be observed. Therefore, a constant market implied volatility and correlation parameter are assumed. Another assumption in the model is a constant recovery rate for the reference obligor. This is in line with the current standard practice of the CDS market.
 
•	The hazard rate process is assumed to be an OU process under the T forward measure, but the pricing formulae are derived under the annuity measure. Formally, this requires a drift adjustment to the hazard rate process that is currently not implemented. We will be implementing an approximation to this drift adjustment in due course and preliminary analysis suggests it does not have a material impact unless correlation is set to very extreme levels. 

Three credit-related risk measurers are implemented in the model. These are the credit spread sensitivity, the default sensitivity, and the correlation sensitivity. The credit spread sensitivity is calculated by shocking the credit spread curve 5bps up. 

The default sensitivity (DS) is defined by setting the reference obligor to default immediately. This is in line with the current definition of all the structure credit derivative products. When the reference obligor defaults at the valuation date, the holder of the CCIRS trade has the right to enter into a swap. Hence the default sensitivity can be calculated straightforwardly as:

(25)	 

The correlation sensitivity is calculated by perturbing the correlation between the hazard rate and the swap rate directly10% up. 

Just like most interest rate models, the dynamic processes involve several parameters, which should be calibrated to the pertinent market information. In the CCIRS model, correlation between the interest rate and the credit is not a market observable. Hence one purpose of the CCIRS model is to provide a method to back out implied correlation information from the market.

When we price a CCIRS trade using the model, we expect that the correlation can be implied from the market quote of another CCIRS trade with the same reference obligor and the same currency. If there is no liquid option market for a given name and a currency, correlation information can be found by proxy to other names. If the implied volatility cannot be found from the market, a historical analysis has to be used to find a reasonable estimate. GRMMR London has proposed a way to conduct such analysis.

As shown in Eq. (22), a series of vanilla European swaptions with almost continuous settlement dates have to be priced.  Under the assumption of a lognormal model, market implied volatilities, which possess skew and smile structures, have to be used so that the swaption prices calculated by the Black’s formula are consistent with the market. In the model, the implied volatilities are calculated via the SABR model, which is the approved stochastic volatility model. The details of the model can be found. The implied volatility for a given strike and a specified term is calculated via Eq. (7).

The methods to determine all the parameters are given in Table 1. They are calibrated to the swaption market, the CDS market, and the CDSO market. The method of pricing a CDSO trade can be found.  As indicated in Table 1, only one parameter   is chosen subjectively. The choice should be monitored and a model risk reserve has to be set up to reflect this uncertainty.
  
Table 1. Method to Determine Parameters
	Parameters	Calibration of the parameters	Comments
Correlation between interest and credit	 
Best effect to calibrate to the CCIRS market. 	Historical data analysis is the last resort.
Interest Rate Dynamics	 
Calibrated to the swaption market via the SABR model. 	
Hazard Rate Dynamics	 
No Calibration. 	Parameter reserve is needed
	 
Calibrated to the CDS market (unconditional default)	Both   and    are only shown in Eq. (11). They are absorbed in the survival probability, which is calibrated from the CDS market.
	 
Calibrated to the CDS market	
	 
Calibrated to the CDSO market.	The volatility of the hazard rate curve is calculated from the volatility of the credit spread, which can be implied by the CDS option.


