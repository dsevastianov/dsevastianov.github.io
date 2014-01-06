Let's start with a zero-coupon bond. This is one of the simplest financial instruments, 
in fact it's just a loan with fixed return date. 
The [classic approach](http://en.wikipedia.org/wiki/Bond_valuation#Stochastic_calculus_approach) 
uses [Martingale pricing](http://en.wikipedia.org/wiki/Martingale_pricing) employing 
random variable for uncertain future rates. I will attempt to do similar valuation with fuzzy numbers.

The goal is to determine present value of the bond: 
$$$ P=\frac{M}{1+i} \(1\)$$$

Here, $M$ is a face value a.k.a value at maturity and $i$ is market interest rate. 
Typically the later will be annual rate which means that for the bond with time to
maturity of several years, the present value is calculated as $P=\frac{M}{(1+i)^{t}}$ 
where $t$ is a number of years.

Rate $i$ is uncertain as it represents some rate corresponding to possible alternative 
investments. These alternatives are numerous and may be spread over the year. In other 
words, investment into bond locks how much money we are going to make on our investment. 
If interest rates will go down over the period of investment, our investment will outperform 
alternatives, or we can even sell the bond on the market for premium as its price will
go up. At the same time, if rates go up we are stuck with inferior investment, or we can 
sell it on discount and try our luck with alternatives.

Let's try fuzzy valuation on [T-bill](http://en.wikipedia.org/wiki/United_States_Treasury_security#Treasury_bill). 
Let's say, we are buying $10,000 T-bill at discount rate of 0.12 percent, which means that 
we will earn $12 over a year. We believe that the rate is not going to be over 0.14 percent, 
it's unlikely that it can be lower than 11, and there prevailing market rate right now is 0.12 percent. 
This can be described by [triangular fuzzy number][fuzzy.fs]: 
$i=[0.0011,0.0012,0.0014]$ Using calculus from [previous post][fuzzy.fs] it is trivial to calculate $P$: 

$P=\frac{\$10,000}{1+[0.0011,0.0012,0.0014]}=[\$9986.02,\$9988.01,\$9989.01]$

Looks slightly simpler than stochastic calculus, right? No assumptions made about the nature of 
[stochastic process](http://en.wikipedia.org/wiki/Short_rate_model) and random distribution either. 
The obvious question, of course, is what do to with this resulting fuzzy number and how it is compatible 
with the price of the bond. After all, the ultimate goal of the whole exercise is to decide if this bond
is worth investing into. There is a range of methods for so-called 
[defuzzification](http://en.wikipedia.org/wiki/Defuzzification) which deserves separate post and discussion.

Now, let's apply fuzzy approach to common bond. The difference is in coupons paid in fixed periods 
of time before the maturity. As an example, let's take 2-year $1,000 bond with coupon rate of 10%. 
It means that we will have 2 coupon payments of $100. Typically, coupon payments are semi-annual,  
I'm using annuals for the sake of simplicity.

There are several approaches to the valuation of bonds. [Arbitrage-free approach][arbitrageFreePricing] 
allows to model a bond by [stripping] the coupons and representing each of them as a zero-coupon bond. 
Each of these bonds will come with its own interest rate corresponding to the date of maturity. 
The nice thing about this approach is that it aligns well with common sense. Indeed, arbitrage-free  
means that if something like that can be done, the price of the bond should reflect it, because 
otherwise it would be possible to make money without risk by creating such synthetic bond out of 
zero-bonds and pocketing difference in price. Obviously, there are various tax-related and operational 
details, including liquidity issues, which would be reflected in the price of synthetic bond which we 
will ignore for the sake of simplicity.

Applying this approach, we can view the bond as a sum of cash flows from all of the coupon payments and 
par value. Now, there are two interest rates involved - for each year. Let's keep $i$ for the first year 
the same as in the first example:  $i_{1}=[0.0011,0.0012,0.0014]$, the second interest rate 
will be represented by the following fuzzy number:  $i_{2}=[0.0008,0.0011,0.0016]$. Notice that I made 
it wider - corresponding uncertainty is bound to be higher for the value further in future. In other 
words, I expect interest rate to be a bit lower two years from now, and higher uncertainty is 
reflected in wider bottom interval of the fuzzy number.

Present value is calculated as
$P =\frac{\$100}{1+[0.0011,0.0012,0.0014]}+\frac{\$1,100}{(1+[0.0008,0.0011,0.0016])^{2}}$
$P =[\$1,196.35; \$1,197.46; \$1198.13] $

Based on my [implementation of fuzzy calculus][fuzzy.fs], the calculation can be made with following code:

[sourcecode language="fsharp"]
let i1 = number(0.0011m,0.0012m,0.0014m)
let i2 = number(0.0008m,0.0011m,0.0016m)
let M = 1000m
let couponRate = 0.1m

let coupon = M * couponRate
let PV = coupon/(1m+i1)+(coupon + M)/Fuzzy.pow(1m+i2, 2.)
[/sourcecode]

Next, I will talk about defuzzification and ways of using these numbers for actual bond valuation.

[prevPost]: http://fuzzyfsharp.wordpress.com/2013/11/07/fuzzy-set-theory-basics/
[fuzzy.fs]: https://github.com/dsevastianov/FSharp.Fuzzy/blob/master/src/FSharp.Fuzzy/Fuzzy.fs
[arbitrageFreePricing]:http://en.wikipedia.org/wiki/Bond_valuation#Arbitrage-free_pricing_approach
[stripping]:http://en.wikipedia.org/wiki/Zero-coupon_bond#Strip_bonds