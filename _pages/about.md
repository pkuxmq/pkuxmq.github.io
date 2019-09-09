---
permalink: /
title: ""
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---



ABOUT ME
------
I am a senior student at Peking University, majoring in computer science and psychology (secondary major). [Curriculum Vitae](https://pkuxmq.github.io/files/CV_MingqingXiao.pdf).

I'm currently in Prof. [Zhouchen Lin](http://www.cis.pku.edu.cn/faculty/vision/zlin/zlin.htm)'s lab, Peking University. My research interests include machine learning and the intersection between machine learning and cognitive science, with emphasis on optimization and computer vision.

In the summer 2019, I was a visiting student in [CCVL (Computational Cognition, Vision, and Learning) lab](https://ccvl.jhu.edu/) at Johns Hopkins University, supervised by Prof. [Alan Yuille](http://www.cs.jhu.edu/~ayuille/).

&nbsp;
&nbsp;
&nbsp;
&nbsp;

RESEARCH PROJECTS
-----
### TDAPNet: Prototype Network with Recurrent Top-Down Attention for Robust Object Classification under Partial Occlussion

- Tackle vulnerability of deep neural networks in occlusion conditions by introducing prototypes, partial matching and top-down attention regulation.
- Learn feature activation prototypes and do partial matching between features and prototypes by estimated attention based on feature dictionary and activation scale.
- Propose top-down attention regulation in convolution layers to reduce the contamination by occlusion with inspiration from neuroscience research.
- Overall Architecture:
![Overall Architecture of TDAPNet](/images/Architecture.jpg)

&nbsp;
&nbsp;
&nbsp;
&nbsp;

### Lifted Proximal Operator Machine

- Training neural networks without gradient.
- Parallelizable among layers.

&emsp;Optimization in standard feed-forward neural network:  
&emsp;&emsp;&emsp;$$\mathop {\min}\limits_{\{W^i\}} l(\phi(W^{n-1}\phi(\cdots\phi(W^2\phi(W^1X^1)))),L)$$  
&emsp;Reformulate as constrained optimization:  
&emsp;&emsp;&emsp;$$\mathop {\min}\limits_{\{W^i\},\{X^i\}} l(X^n,L)$$  
&emsp;&emsp;&emsp;$$s.t.		X^i=\phi(W^{i-1}X^{i-1}),i=2,3,\cdots,n$$  
&emsp;Rewrite the activation function as an equivalent proximal operator:  
&emsp;&emsp;&emsp;$$\mathop{argmin}\limits_{X^i}1^Tf(X^i)1+1^Tg(W^{i-1}X^{i-1})1+\frac{1}{2}||X^i-W^{i-1}X^{i-1}||_F^2$$  
&emsp;&emsp;where $f(X)=\int_{0}^{x}(\phi^{-1}(y)-y)dy,g(X)=\int_{0}^{x}(\phi(y)-y)dy$  
&emsp;Add the penalty and the objective function is:  
&emsp;&emsp;&emsp;$$\mathop {\min}\limits_{\{W^i\},\{X^i\}} l(X^n,L)+\sum\limits_{i=2}^n\mu_i(1^Tf(X^i)1+1^Tg(W^{i-1}X^{i-1})1+\frac{1}{2}||X^i-W^{i-1}X^{i-1}||_F^2)$$  
&emsp;Use block coordinate descent algorithm to solve the optimization problem.
