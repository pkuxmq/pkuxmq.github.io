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

My research interests lie in the general area of machine learning, including deep learning, optimization, statistical modeling, and interpretable models, as well as their application in computer vision, image processing, and intersection with neuroscience.

I'm currently a research intern at Microsoft Research Asia Machine Learning Group led by Dr. [Tie-Yan Liu](https://www.microsoft.com/en-us/research/people/tyliu/). My supervisor at Peking University is Prof. [Zhouchen Lin](http://www.cis.pku.edu.cn/faculty/vision/zlin/zlin.htm).

In the summer 2019, I was a visiting student at [CCVL (Computational Cognition, Vision, and Learning) lab](https://ccvl.jhu.edu/) in Johns Hopkins University, supervised by Prof. [Alan Yuille](http://www.cs.jhu.edu/~ayuille/).

&nbsp;
&nbsp;
&nbsp;
&nbsp;

Publications
------
**Mingqing Xiao**; Shuxin Zheng; Chang Liu; Di He; Jiang Bian; Guolin Ke; Zhouchen Lin; and Tie-Yan Liu. Invertible Image Rescaling. In submission.

**Mingqing Xiao**; Adam Kortylewski; Ruihai Wu; Siyuan Qiao; Wei Shen; and Alan Yuille. 2019. TDAPNet: Prototype Network with Recurrent Top-Down Attention for Robust Object Classification under Partial Occlusion. [arXiv preprint arXiv:1909.03879](https://arxiv.org/abs/1909.03879). In submission.

Jia Li; **Mingqing Xiao**; Cong Fang; Yue Dai; Chao Xu; and Zhouchen Lin. Training Deep Neural Networks by Lifted Proximal Operator Machines. In submision to IEEE Trans. Pattern Analysis and Machine Intelligence.

RESEARCH PROJECTS
-----
### Invertible Image Rescaling

- Model image upscaling and downscaling from a novel perspective, i.e. invertible bijective distribution transformation, by embedding lost high-frequency information into a latent variable during image downscaling, which largely mitigates the ill-posed problem of image upscaling after downscaling.
- Propose Invertible Rescaling Net (IRN) with deliberate model design and efficient training objectives.
- Significantly boost the performance of upscaling reconstruction from downscaled images both quantitatively and qualitatively. PSNR boost can be up to 8.76 dB when compared with the state-of-the-art super-resolution methods after bicubic downscaling. Meanwhile, model is light-weight and efficient.
- Overall Architecture:
![Overall Architecture of IRN](/images/InvSR.png)

&nbsp;
&nbsp;
&nbsp;
&nbsp;

### TDAPNet: Prototype Network with Recurrent Top-Down Attention for Robust Object Classification under Partial Occlussion \[[arXiv:1909.03879](https://arxiv.org/abs/1909.03879)\]

- Tackle vulnerability of deep neural networks under novel occlusion conditions that do not appear in training data by introducing prototypes, partial matching and top-down modulation.
- Improves the robustness of DCNNs with increase of 11% on PASCAL3D+ and 17.2% on MNIST for average classification accuracy under different simulated occlusion conditions. The robustness can also generalize to real novel occlusion in COCO and under dataset transfer.
- Overall Architecture:
![Overall Architecture of TDAPNet](/images/Architecture.jpg)

&nbsp;
&nbsp;
&nbsp;
&nbsp;

### Lifted Proximal Operator Machine

- Relax optimization for neural networks to a multi-convex problem.
- Train neural networks without gradient.
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
