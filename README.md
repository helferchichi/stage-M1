# stage-M1
\documentclass[a4paper,11pt]{article}
\usepackage[main=english,french]{babel}
\usepackage{fullpage}
\usepackage[utf8]{inputenc}
\usepackage{iflang}
\usepackage{ifthen}
\usepackage{color}
\usepackage{parskip}
\setlength{\parindent}{15pt}
\usepackage{comment}
 
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{amssymb} 
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage{enumerate}
\usepackage{caption}
\usepackage{graphicx}
\usepackage{mathtools}


\newcommand{\x}{\ensuremath{\mathbf x}}
\newcommand{\y}{\ensuremath{\mathbf y}}
\newcommand{\z}{\ensuremath{\mathbf z}}
\def\bw{\mathbf{w}}
\def\bx{\mathbf{x}}
\def\by{\mathbf{y}}
\def\bz{\mathbf{z}}
\def\bu{\mathbf{u}}
\def\bv{\mathbf{v}}
\def\bI{\mathbf{I}}
\def\bS{\mathbf{S}}
\def\bG{\mathbf{G}}
\def\bV{\mathbf{V}}
\def\RR{\mathbf{R}}
\def\bF{\mathbf{F}}
\newtheorem{exercise}{Exercise}
\def\quest{\vspace{0.25 cm} \noindent }
\def\subquest{\vspace{0.2cm}}
\newcommand{\integrale}[2]{\ensuremath{\displaystyle{\int_{#1}^{#2}}}}
\begin{document}

\section{Formulation du problème}
Le problème au quel on s'interesse est le suivant:\\
On cherche minimiser la fonctionnel suivante: $ \Psi (\mu) = - log\, (det\, M(\mu) ) $\\
où $ M = \integrale{}{} f(x)^\top f(x) \mu(dx)$ est la matrice d'information.\\
Pour cela on à besoin de la première variation de $\Psi$ pour écrire l'equation de continuité. Celle-ci est donnée dans [Steepest descent algorithms in a space
of measures, Molchanov Zuyev]:
$$\frac{\delta \Psi}{\delta \mu} = -f(x) M(\mu)^{-1}f(x)^\top$$
l'equation de continuité est ainsi:
$$\partial_t\mu_t - \nabla\, . \,\big(\,\mu_t \, \nabla(\,\frac{\delta \Psi}{\delta \mu}\,)\,\big) = 0$$
tout calcul fait, on trouve que $\nabla(\,\frac{\delta \Psi}{\delta \mu}\,) = -2\,\nabla f(x)^\top \, M(\mu_t)^{-1} \,f(x) $.\\

\section{Geodesic convexity}
La geodesic convexity permet de garantir la convergence asymptotique vers un minimum.
On dit que F est geodesiquement convexe si $t \to F(\mu_t)$ est convexe pour toute geodesique $ t\to \mu_t$.\\
On sait que les géodesiques sont de la forme suivante: $$t \to \mu_t = ((1-t)Id + t T)_{\#\mu_0}$$ où T est le plan de transport entre $\mu_0$ et $\mu_1$.\\
Ceci étant, $$\Psi(\mu_t) = -log\,( det M(\mu_t) ) $$
$$M(\mu_t) = \integrale{}{} f(x)^t f(x) \mu_t(dx) = \integrale{}{} F(\,(1-t)x + t T(x)\,) \mu_0(dx)$$
avec $F(x) = f(x)^\top f(x)$. Si on note $g_x(t) = (1-t)x + tT(x)$ alors: $$(F\circ g_x)'(t) = (df_{g(t)}.g'(t))^\top f(g_x(t)) + f(g_x(t))^\top \, (df_{g(t)} . g'(t))$$
Dans notre situation: $f(x) = (x, x^2, x^3)$, $ df(x).h =(1, 2h, 3h^2)  $\\
Ainsi:
$$ (F\circ g_x)'(t) = (1, 2g'(t), 3g'(t)^2)^\top (g_x(t), g_x(t)^2, g_x(t)^3) +  (g_x(t), g_x(t)^2, g_x(t)^3)^\top (1, 2g'(t), 3g'(t)^2)   $$
tout calcul fait, on trouve:
$$\Psi(\mu_t)' = - Tr(M^{-1}(\mu_t) \integrale{}{} (F\circ g_x)'(t) d\mu_0(x) )$$
Vu les résultats de simulation, on pourrait se dire qu'on n'a pas geodesique convexité (ni convexité par rapport aux geodesiques generalisées) car cela donnerai une convergence exponentielle en temps ce qu'on n'a pas l'air d'avoir.

\section{Birth Death}
L'article traite d'un potentiel ayant uen forme particulière (somme d'une energie potentiel et d'un terme d'interaction). Ce potentiel V correspondrait à $\frac{\delta \Psi}{\delta \mu}$ dans notre problème qui, a priori, n'a pas la même forme

\end{document}
