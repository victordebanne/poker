# poker

## calcul de la probabilité d'avoir la meilleure main sachant les cartes. 

$$
\begin{align}
&\mathbb{P} (\text{gagner} | \text{cartes}) = 
\sum_{i = 0}^N \mathbb{P}(c_i \ \text{gagnant} | \text{cartes}) \cdot \mathbb{P}(c_i | \text{cartes}) \\
&\text{avec c les différentes combinaisons possibles (paire, carré, couleur...)}
\end{align}
$$

la probabilité d'obtenir une carte $x$ sachant les cartes (cartes du joueur et cartes sur le plateau) : 

$$
\begin{align}
\text{avec} \quad E \quad \text{l'ensemble des cartes connues} \\
\text{et} \quad F \quad \text{l'ensemble des cartes non connues.}\\
\mathbb{P}(x|E) =
\begin{cases}
\frac{1}{52 - \lvert E \rvert} \quad \text{si} \quad x \notin E \\
1 \quad \text{sinon}
\end{cases}
\end{align}
$$

### probabilité du tirage d'une combinaison c parmi n cartes sans remise

$$
\begin{align}
&\text{probabilité de tirer x puis y ou y puis x parmi n sans remise} \\
\mathbb{P}(x\ \text{puis} \ y) &= \mathbb{P}(x|n) \cdot \mathbb{P}(y|n - 1) = \frac{1}{n} \cdot \frac{1}{n - 1} \\
\mathbb{P}(y\ \text{puis} \ x) &= \mathbb{P}(y|n) \cdot \mathbb{P}(x|n - 1) = \frac{1}{n} \cdot \frac{1}{n - 1} \\
\mathbb{P}(x\ \text{puis} \ y)\cup \mathbb{P}(y\ \text{puis} \ x) &= \frac{2}{n(n-1)} \\
&\text{on peut généraliser pour un tirage d'une combinaison} \ c \ \text{avec} \ k \  \text{cartes sans remise} \\
\mathbb{P}(c) &= k!\prod_{i = 0}^{k - 1}\frac{1}{n-i}
\end{align}
$$

### probabilité du tirage d'une combinaison c parmi n cartes sur t tirages sachant les cartes sans remise

$$
\mathbb{P}(c | E) = \mathbb{P}(c - c \cap E) 
$$

ici, nous décomposons en plusieurs combinaisons, ce que l'on considèrerait une combinaison. 
par exemple : 
la combinaison paire d'as se décompose en : 

$$
\begin{align}
&A♦ + A♥ \\
&A♦ + A♠ \\
&A♦ + A♣ \\
&A♥ + A♠ \\
&A♥ + A♣ \\
&A♠ + A♣ \\
\text{donc} \ &13 \times \binom{4}{2} \ \text{combinaisons de paires}
\end{align}
$$


on peut donc calculer la probabilité avant distribution d'obtenir chaque combinaison. 

$$
\begin{align}
&\text{probabilité de tirer x et y parmi n cartes sans remise sur 3 tirages} \\
P(x \ \text{puis} \ y \ \text{puis rien}) &= \frac{1}{n}\cdot\frac{1}{n-1} \cdot \frac{n - 2}{n - 2} = \frac{1}{n}\cdot\frac{1}{n-1}\\
P(y \ \text{puis} \ x \ \text{puis rien}) &= \frac{1}{n}\cdot\frac{1}{n-1} \cdot \frac{n - 2}{n - 2} = \frac{1}{n}\cdot\frac{1}{n-1}\\
P(x \ \text{puis rien puis} \ y) &= \frac{1}{n}\cdot\frac{n-2}{n - 1}\cdot\frac{1}{n-2}  = \frac{1}{n}\cdot\frac{1}{n-1}\\
P(y \ \text{puis rien puis} \ x) &= \frac{1}{n}\cdot\frac{n-2}{n - 1}\cdot\frac{1}{n-2}  = \frac{1}{n}\cdot\frac{1}{n-1}\\
P(\text{rien puis} \ x \ \text{puis} \ y) &= \frac{n-2}{n}\cdot\frac{1}{n - 1}\cdot\frac{1}{n-2}  = \frac{1}{n}\cdot\frac{1}{n-1}\\
P(\text{rien puis} \ y \ \text{puis} \ x) &= \frac{n-2}{n}\cdot\frac{1}{n - 1}\cdot\frac{1}{n-2}  = \frac{1}{n}\cdot\frac{1}{n-1}\\
\end{align}
$$

$$
\begin{align}
&\text{on généralise avec une combinaison c de k cartes parmi n cartes sur t tirages avec t > k}\\
&\text{par exemple pour t = 4 et k = 2}\\
&\binom{t}{k}
\begin{cases}
k! \times &1 \ 1 \ 0 \ 0\\
k! \times&1 \ 0 \ 1 \ 0\\
k! \times&1 \ 0 \ 0 \ 1\\
k! \times&0 \ 0 \ 1 \ 1\\
k! \times&0 \ 1 \ 0 \ 1\\
k! \times&0 \ 1 \ 1 \ 0\\
\end{cases} 
\\
\end{align}
$$

$$
\begin{align}
&\text{soit} \ \sigma \ \text{une séquence}\ (x_1, c, x_2, \cdots, x_3) \\
\mathbb{P}(\sigma) &= \prod_{i=0}^{t-1}
\frac{
\begin{cases}
1 \ \text{si} \ \sigma_i = x_i \\
n - i - (k -l_i) \ \text{sinon, avec} \ l_i, \ \text{le nombre de} \ x \ \text{passés}
\end{cases}
}
{n - i}
\\
\text{on a}\\
n - i - k - l_i &=(n - k) - (i - l_i) \ \text{avec} \ (i - l_i), \ \text{le nombre de}\ c \ \text{restants dans la séquence.}\\
\text{on trouve donc}\\
\mathbb{P}(\sigma) &= \frac{\prod_{j = k}^{t-1} n - j}{\prod_{i=0}^{t-1} n - i} = \frac{1}{\prod_{i=0}^{k-1} n - i} \cdot \frac{\prod_{j=k}^{t-1} n - i}{\prod_{i=k}^{t-1} n - i} = \boxed{\prod_{i=0}^{k-1}\frac{1}{n - i}}
\end{align}
$$

$$
\begin{align}
\mathbb{P}(c) &=
\binom{t}{k} k!\prod_{i = 0}^{k - 1}\frac{1}{n-i}\\
\prod_{i = 0}^{k - 1}n-i &= \frac{n!}{(n-k)!}\\
\text{d'ou}\quad k!\prod_{i = 0}^{k - 1}\frac{1}{n-i} &= \frac{k!(n-k)!}{n!} = \frac{1}{\binom{n}{k}}\\
\text{d'ou} \quad \mathbb{P}(c) &= \frac{\binom{t}{k}}{\binom{n}{k}}\\
\end{align}
$$

### demonstration : les cartes distribuées ne changent pas la probabilité d'obtenir une carte x

$$
\begin{align}
&\text{Probabilité de tirer une carte x parmi n cartes sachant que k cartes ont été brulées} \\
&\frac{1}{n - 1} \cdot (1 - \frac{1}{n}) = \frac{1}{n}
\\
\\
&\text{on généralise : }
\\
\\
&\frac{1}{n - k} \cdot (1 - \frac{1}{n - k + 1}) = \frac{1}{n - k + 1}
\\
\\
&\text{d'ou}
\\
&\frac{1}{n -k} \prod_{i = 0}^{k-1}(1-\frac{1}{n-i}) \\ \\
= &\frac{1}{n -k + 1} \prod_{i = 0}^{k-2}(1-\frac{1}{n-i})\\ \\
= &\frac{1}{n -k + k}  \\ \\
= &\quad\boxed{\frac{1}{n}}\\ \\
&\text{d'ou} \\
&\mathbb{P}(x|k) = \frac{1}{n} \\ \\
&\text{d'une autre façon, si n - 1 cartes sont brulées, la probabilité que la carte non brulée soit x est} \quad \frac{1}{n} 
\end{align}
$$

## Application aux combinaisons du poker

Les mains du poker sont composées de 1 à 5 cartes

Avant la distribution, on peut chercher à calculer la probabilité d'obtenir une main spécifique. 

il s'agit donc de la probabilté d'obtenir une combinaison $c$, de composée de $k$ cartes sur $t$ tirages parmi $n$ cartes. 

soit les combinaisons $c_1, \cdots, c_5$. 

$$
\mathbb{P}(c|t,n,k) = \frac{\binom{t}{k}}{\binom{n}{k}}
$$

$$
\text{pour} \ c_1
$$

$$
\mathbb{P}(c_1|7,52,1) = \frac{\binom{7}{2}}{\binom{52}{2}} = 0.1346153846153846
$$

la probabilité d'avoir un séquence exacte sur un certain nombre de tirages n'impose rien sur les autres cartes.

donc pour obtenir la probabilité que $t$ tirages aient exactement un certain nombre d'As, il faut imposer une contrainte sur les cartes n'appartenant pas à la séquence. 

donc la probabilité pour que dans une séquence donnée contienne A♦ et A♥ est la probabilité de la combinaison A♦ + A♥ sur $t$ tirages parmi $n$ cartes par la probabilité sur $(t - k)$ tirages de tirer $(t - k)$ cartes parmi $(n-k)$ cartes. 

$$
\begin{align}
&\text{appelons} \ c \ \text{la combinaison recherchée et } \ \overline{c} \ \text{la combinaison complémentaire avec contrainte}. \\
&\mathbb{P}(c) = \frac{\binom{t}{k}}{\binom{n}{k}}\\
&\mathbb{P}(\overline{c}) = \frac{\binom{t-k}{t-k}}{\binom{n-k}{t-k}}\\
\end{align}
$$

calcul de la probabilité d'avoir exactement une paire d'As:

$$
\begin{align}
&\mathbb{P}(\text{exactement paire d'As}) &= \text{(nombre de combinaisons d'As)} \cdot P(\text{contient paire d'As}|n, k, t) \cdot \text{(nombre de combinaisons sans As)} \cdot P(\text{contient aucun as}|n-k, t-k, t-k) \\
&= \binom{4}{2} \cdot \frac{\binom{7}{2}}{\binom{52}{2}} \cdot \binom{48}{5} \cdot \frac{1}{\binom{50}{5}}
\end{align}
$$

$$
\mathbb{P}(\text{exactement} \  k x_i|t, k, n) = \binom{A}{k} \cdot \frac{\binom{t}{k}}{\binom{n}{k}} \cdot \binom{n-A}{t-k} \cdot \frac{1}{\binom{n-k}{t-k}}
$$

$$
=\binom{A}{k} \cdot \binom{n-A}{t-k} \cdot
\frac{t!k!(n-k)!}{k!(t-k)!n!} \cdot
\frac{(t-k)!(n-k-(t - k))!}{(n-k)!}
= \binom{A}{k} \cdot \binom{n-A}{t-k} \cdot \frac{t!(n-t)!}{n!}
= \boxed{\frac{\binom{A}{k} \cdot \binom{n-A}{t-k}}{\binom{n}{t}}}
$$

$$
\text{il s'agit de la loi hypergéométrique}
$$

$$
\begin{align}
\mathbb{P}(X \ge k|t,n,A) &=  \mathbb{P}(X = k|t,n,A) + \mathbb{P}(X = k+1|t,n,A)+\cdots+\mathbb{P}(X = A|t,n,A)\\
&= \sum_{i=k}^{A} \frac{\binom{A}{i} \cdot \binom{n-A}{t-i}}{\binom{n}{t}} \\
\end{align}
$$

$$
\begin{align}
&\text{avec} \binom{N_i}{c_i} \ \text{le nombre de cartes favorables de} \ c_i \ \text{dans} \ n  \\
&\text{et} \quad c = \sum_{i=0}^{m}c_i\\
&\mathbb{P}(c|N, n, t) = 
\left[\prod_{i=1}^{m} \binom{N_i}{\lvert c_i \rvert} \cdot
\frac{\binom{t-\sum_{j=1}^{i}\lvert c_j \rvert}{\lvert c_i \rvert}}
{\binom{n-(\sum_{j=1}^{i}\lvert c_j \rvert) + \lvert c_1 \rvert}{\lvert c_i \rvert}}\right] \cdot
\frac{\binom{n - \sum_{i=1}^{m}N_i}{t-\sum_{i=1}^{m}\lvert c_i \rvert}}
{\binom{n - \sum_{i=1}^{m}\lvert c_i \rvert}{t-\sum_{i=1}^{m}\lvert c_i \rvert}}
\end{align}
$$

$$
\begin{align}
&\text{On travaille dans l’espace probabiliste uniforme des mains de t cartes parmi n} \\
&\text{et toutes les décompositions sont interprétées comme des probabilités conditionnelles définies sur ce même espace.} \\ \\
&P(\text{exactement une paire}) = P(\text{une paire}|n, t) \cdot P(\text{aucune paire}|n - 2, t - 2) \\ \\
&\text{on impose donc une contrainte sur les cartes restantes}\\
&\text{il y a} \ 4 \ \text{cartes d'un type (A = nombre de cartes d'un type)}  \\
&\text{chaque carte ne doit pas être appairée}\\
&\text{exemple pour} \ t = 3, n = 52, A = 4 \\ \\
&P(\text{aucune paire}) = 1 \cdot \frac{51 - 3}{51} \cdot \frac{50 - 6}{50}\\  \\
&\text{on généralise} \\
&P(\text{aucune paire}|A, n,t) = \prod_{i = 0}^{t - 1} \frac{n - i - (A- 1)i}{n - i}
=\prod_{i = 0}^{t - 1} \frac{n - Ai}{n - i}\\
&\text{d'ou} \ P(\text{exactement une paire}) = 
\binom{13}{1} \cdot \frac{\binom{A}{k} \binom{n - A}{t - k}}{\binom{n}{t}} \cdot \prod_{i = 0}^{t - 1 - k} \frac{n - k - Ai-2}{n - k - i}
\end{align}
$$

$$
\begin{align}\iff 
P(\text{aucune paire}|A, n,t)
&=\prod_{i = 0}^{t - 1} \frac{n - Ai}{n - i} = \prod_{i = 0}^{t - 1} \frac{1}{n - i}\cdot \prod_{i = 0}^{t - 1}n - Ai \\
&= \frac{(n - t)!}{n!} \cdot A^t\frac{\frac{n}{A}!}{(\frac{n}{A}-t)!} \\
&= \frac{(n - t)!\ t!}{n!\ t!} \cdot A^t\frac{\frac{n}{A}!\ t!}{(\frac{n}{A}-t)!\ t!} \\
&= \frac{1}{\binom{n}{t}\ t!} \cdot A^t \binom{\frac{n}{A}}{t} \ t! \\
&= A^t \frac{\binom{\frac{n}{A}}{t}}{\binom{n}{t}} 
\end{align}
$$




