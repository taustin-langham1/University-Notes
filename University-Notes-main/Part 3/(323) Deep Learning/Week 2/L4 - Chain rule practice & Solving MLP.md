

## Differentiation - Introducing the Chain Rule

One of the important ones like: linearity, product, ect.
quotient -> use the little trick x^-1 = something

allows you to differentiate functions of this form:

$\huge y = f(g(x))$

(composite functions)


things like:

$\huge y = e^{3x^{2}+5}$

$\huge (x^3 - 3x + 2)^5$

$\huge y = sin(tan x)$

can you see the g(x) within the f(x)?  f(g(x))

so we make a substitution:

u becomes the g(x) 'the function within'

so, follow $\huge u$: 
$\huge u = g (x) \;\;\; \frac {dy}{dx} = g'(x)$

$\huge y = f(u)  \;\;\; \frac {dy}{dx} = f'(u)$

so the dy/dx would be the product of these two things

$\huge \frac{dy}{dx} = \frac {dy}{du} \cdot \frac {du}{dx}$ 

$\huge = g'(x) f(g(x))$

so the idea is that these 'fractions' cancel eachother out, but like not really, yet thats how we will see it

-> its not a fraction in the true sense of the word, its a limit, but can sometimes work similarly 

### Examples of using the Chain Rule
#### Part 1 

find $\frac {dy}{dx}$ for 

1) $\huge y = (2x + 7)^5$


2) $\huge y = (3 + x)^4$


3) $\huge y = (x^3-3x + 2)^5$


4) $\huge y = \sqrt{8x - 3}$


5) $\huge y = \frac {1}{x + 1}$


6) $\huge y = \frac {3}{\sqrt {5x+2}}$


## Solving MLP

1) solving
2) where do update algorithms come from, and how we derive them



$\huge L(y,\hat u) = \frac {1}{2n_s}\sum_l^{n_s} (y_i - \hat y_i)$




