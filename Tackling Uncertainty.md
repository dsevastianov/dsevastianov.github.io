##What is uncertainty?

Ultimately, the goal of any financial analysis is prediction, whether it's prediction of stock prices, earnings, or health of economy. To predict, one has to harness uncertainties of the system under analysis.

Classical probability theory focuses on so-called **stochastic** uncertainty, in other words, an uncertainty related to randomness of the events. The most common example of such uncertainty would be flipping a coin. There is no doubt that stochastic uncertainty plays critical role in wide range of fields, from quantum mechanics to economics. Statistics provides invaluable toolbox for dealing with this type of uncertainty.

##When classics is not enough

And than there is another kind of uncertainty sometimes called [**epistemic**](http://en.wikipedia.org/wiki/Uncertainty_quantification). In short, this is an uncertainty of insufficient information about the system. 

One example of such uncertainty is **human judgment**. By now it's well-known that humans are not always rational in their behavior. One can argue that the whole concept of technical stock analysis is primarily an attempt to somehow describe irrationality of market behavior.

Further, in many cases it is impossible to collect enough data to apply statistical methods reliably. Another example of **epistemic uncertainty** is how macro-economics attempts to forecast future development on historical basis. More often than not such extrapolation is not reliable, first of all because economics studies ever-changing system where basic assumptions easily become obsolete. Markets are famous for their ability to correct themselves whenever certain theory tries to capture and capitalize on some particular feature of their behavior.

Of course, presence of **epistemic uncertainty** is not limited to finance. Health science, for example, faces a lot of that as well. It is notoriously hard to treat such astonishingly complex systems as human organisms as even roughly the same.

If we go all philosophical about this, epistemic uncertainty is inescapable. One of the outcomes of <a href="http://en.wikipedia.org/wiki/Kurt_G%C3%B6del#The_Incompleteness_Theorem">The Incompleteness Theorem</a> is that any system, any model has some intrinsic uncertainty hiding behind original assumptions or lurking in depth of the language chosen for its description. What makes a model successful is its ability to capture important information and produce useful results.

##Enter Fuzzy Sets Theory

So are there any methods and theories to deal with this elephant in the room? 

Well, plenty. Surprisingly, they remain out of the scope of mainstream education system and generally unknown to the graduates with major in applied mathematics. Meanwhile, methods of fuzzy logic, for instance, are widely applied in <a href="http://en.wikipedia.org/wiki/Fuzzy_control_system">engineering</a>. Have a look at your favorite rice cooker. My <a href="http://www.zojirushi.com/products/nsyac">Zojirushi </a>proudly sports 'Fuzzy Logic technology' label.

Any experienced programmer knows how important it is to be explicit about all of the details of the modeled domain. Soft computing allows to be explicit about non-stochastic uncertainties when dealing with uncertainty and provides some unique advantages in calculation complexity.

In the next post, I'll go over basic concepts of Fuzzy Sets theory including basics of fuzzy set mathematics.
