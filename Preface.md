##About myself

I am a professional software developer with background in finance and fuzzy mathematics. I participated and published 15 papers dedicated to the application of fuzzy mathematics in finance and other fields.

Also, I'm a big fan of <a href="http://en.wikipedia.org/wiki/F_Sharp_(programming_language)">F# programming language</a>.

This blog series is devoted to soft computing and its application in finance. It is also my attempt to catch up with the science and refresh it in my head. My goal is to popularize some of the more arcane theories and methods of fuzzy and interval mathematics and demonstrate how they can be applied in finance.

Also, this is not the first attempt. I tried to describe one of the applications of fuzzy sets theory to the very important problem of <a href="http://multicriteria.blogspot.com/2006/10/if-decision-problem-is-not-multiple.html">choosing the right cat</a> in 2006 (ouch!) .

##Code
All code mentioned in this series is available in the <a href="https://github.com/dsevastianov/FSharp.Fuzzy">Github project</a>. It also available as a <a href="https://www.nuget.org/packages/FSharp.Fuzzy/">Nuget package</a>. <a href="http://dsevastianov.github.io/FSharp.Fuzzy/">Here</a> is project home page and documentation.

##Acknowledgments
First of all, my eternal gratitude goes to my parents, Pavel Sevastianov and Ludmila Dymova, professors of [Technical University of Czestochowa](http://www.pcz.pl/english/), who are known world-wide for their contribution in Soft Computing. In fact, my inspiration for the series is driven in part by <a href="http://www.springer.com/engineering/computational+intelligence+and+complexity/book/978-3-642-17718-7">this book </a> by my mother.

Huge thanks to [Don Syme](http://research.microsoft.com/en-us/people/dsyme/) for inventing wonderful F# language, which I'm sure on its way to become one of the major programming languages in near future.

Kudos to Paulmichael Blasucci for <a href="https://github.com/fsprojects/FSharp.ProjectScaffold">Fsharp.ProjectScaffold</a> which saved me tons of time on setting up Github project and Fake build as well as to Tomas Petricek for <a href="https://github.com/tpetricek/FSharp.Formatting">FSharp.Formatting</a> library indispensable in producing project documentation.

##Soft computing
We hear so much about complexity and sophistication of financial systems: risk evaluation,  complex hedging strategies, high frequency trading, credit risk derivative modeling - it all sounds very serious and scientific. Common wisdom on the subject is that this complexity is a primary reason for the financial crisis.

However, it is not the complexity itself that shook the world financial system. The credit crunch is also a reflection of crisis of science in finance and economics. It is enough to look at <a href="http://en.wikipedia.org/wiki/Value_at_risk#Criticism">discussion</a> around Value at Risk to clearly see deep issues in the very basic assumptions made by financial professionals when evaluating risk. Anyone familiar with the field knows the name of <a href="http://en.wikipedia.org/wiki/Nassim_Nicholas_Taleb">Nassim Taleb</a> and his fervent critique of wide-spread methods of risk evaluation. 

It might sound controversial, but in fact economics is quite conservative when it comes to mathematical apparatus it employs. Despite all the hype around creativity of hedge fund wizards, they stick to <a href="http://en.wikipedia.org/wiki/Bayesian_probability">the most classic probability interpretation</a>. In fact, the same is true for Big Data analysis, Machine Learning and other hot fields of computing - western academia keeps ignoring Soft Computing even though most of the original work came from USA.

Here I will talk about some interesting theories and techniques still finding their way into mainstream financial analysis while being widely accepted in engineering and other fields for a long time.

##The list of posts
* [**Tackling uncertainty**](http://fuzzyfsharp.wordpress.com/2013/11/04/uncertainty/) - what kinds of uncertainty we have to deal with and how.
* [**Fuzzy set theory basics**](http://fuzzyfsharp.wordpress.com/2013/11/07/fuzzy-set-theory-basics/) - quick introduction to some of the most useful parts of interval and fuzzy mathematics.
* **[Simple bond valuation](http://fuzzyfsharp.wordpress.com/2013/12/09/simple-bond-valuation/)** - an application of fuzzy sets to bond valuation with examples.
* **[Defuzzification](http://fuzzyfsharp.wordpress.com/2013/12/24/defuzzification/)** - discussion of ways to reason about fuzzy sets.
