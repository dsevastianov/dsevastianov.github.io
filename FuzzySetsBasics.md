In this post, I'll be going over basic definitions of fuzzy set theory 
without getting into too much of the abstract mathematics. I want to 
stress this: my goal is to talk in layman terms about most useful parts of otherwise huge field.

Fuzzy set theory was first introduced by 
[Lotfi A Zadeh](http://en.wikipedia.org/wiki/Lotfi_Asker_Zadeh) in 1965 in his 
paper [Fuzzy Sets](http://www-bisc.cs.berkeley.edu/Zadeh-1965.pdf).

[Fuzzy set](http://en.wikipedia.org/wiki/Fuzzy_set) is a set whose elements can have different
grades of membership. For classical set, this grade is either 1 or 0, in other words, 
either an element belongs to a set, or not. For fuzzy set, this grade can take any value between 0 and 1.

Here is how membership function of fuzzy set typically looks like.

![Figure 1: Trapezoid fuzzy set][alpha-levels]

Here, X=2 has grade of membership $\mu$=1, in other words, it definitely belongs to the fuzzy set. 
X=6 has $\mu$=0 so it doesn't belong to the fuzzy set. X=4, however, has $\mu$=0.5. It effectively 
means that it is not known whether X=4 belongs to the set or not. Also, note those horizontal lines 
on the picture. They correspond to so-called $\alpha$-levels and represent the part of the fuzzy set 
with the same grade of membership, also known as $\alpha$-cut.

It has to be noted that the membership function can have any form, the trapezoid just happens to 
be one of the most useful.

Example:
Let's say, we are trying to define a class of all people of medium height. We can say than that people 
over 6 feet are definitely tall and don't belong to the class, as well as those under 5 feet. Further, 
we may come to conclusion that people between 5'6'' and 5'8'' are definitely of medium height. In this 
case, corresponding membership function would look like this:
<a href="http://fuzzyfsharp.files.wordpress.com/2013/11/height.png"><img class="size-full wp-image" id="i-107" alt="Image" src="http://fuzzyfsharp.files.wordpress.com/2013/11/height.png?w=407" /></a>
So, for example, Ann being 5'7" is definitely of medium height, it is not clear if Bob of 5'10" 
is of medium height, and Christine of 6'2" is definitely not of medium height.
[Fuzzy number](http://en.wikipedia.org/wiki/Fuzzy_number) can be defined 
(according to [Dubois and Prade](http://www.tandfonline.com/doi/abs/10.1080/00207727808941724#.Unv8U_leZ8E)) 
as a fuzzy set whose highest membership values are clustered around a given real number called 
**mean value**. Note that the membership function doesn't have to be symmetric.

<a href="http://fuzzyfsharp.files.wordpress.com/2013/11/triangular.png"><img class="size-full wp-image" id="i-83" alt="Image" src="http://fuzzyfsharp.files.wordpress.com/2013/11/triangular.png?w=266" /></a>

Now, what kind of operations can be done over such numbers? In fuzzy mathematics, it is proven that 
operations on fuzzy sets can be represented as operations on the set of crisp (i.e. non-fuzzy, 
conventional) intervals corresponding to their $\alpha$-cuts. For example, 
in order to add two fuzzy numbers one can add intervals on each $\alpha$-level 
and assemble resulting fuzzy number out of the results.

Which brings us to the [interval arithmetic](http://en.wikipedia.org/wiki/Interval_arithmetic).

In fact, there are several different definitions of interval arithmetic, the most useful and the simplest one is following:

Addition:  $[a_{1},a_{2}] + [b_{1}, b_{2}]=[a_{1}+b_{1},a_{2} + b_{2}]$

Subtraction: $[a_{1},a_{2}] - [b_{1}, b_{2}]=[a_{1}-b_{2},a_{2} - b_{1}]$

Multiplication: $[a_{1},a_{2}] * [b_{1}, b_{2}]=[min(a_{1}b_{1},a_{2}b_{2},a_{1}b_{2},a_{2}b_{1}),max(a_{1}b_{1},a_{2}b_{2},a_{1}b_{2},a_{2}b_{1})]$

Division: $[a_{1},a_{2}]/[b_{1},b_{2}]=[a_{1},a_{2}]*[1/b_{2},1/b_{1}], 0 \notin [b_{1},b_{2}]$

Pretty simple, right?

Тhe formulas for addition, subtraction, and division are in fact should look similar to the formula for multiplication, 
but it is easy to prove that simpler formulas work in these cases. In plain English, these formulas reflect 
fundamental law of interval operations - they always should produce widest possible intervals. Because of that, 
interval arithmetic has one very inconvenient property called **excess width effect**. It means that widths of 
intervals grow rapidly with application of operations. One of the annoying side-effects of this property is 
that different representations of the same function can produce different results.  Not surprisingly, it 
limits applicability of interval methods when it comes to more complex algebra. However, interval arithmetic 
is a very useful tool, which I'll demonstrate in following posts.

Full F# library of fuzzy and interval calculus is available [here](http://dsevastianov.github.io/FSharp.Fuzzy/).

![alpha-levels]: content/img/fuzzy-set.png
![alpha-levels]: content/img/fuzzy-set.png
