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
P(x \ \text{puis} \ y \ \text{puis rien}) &= \frac{1}{n}\cdot\frac{1}{n-1} \cdot \frac{n - 2}{n - 2}\\
P(y \ \text{puis} \ x \ \text{puis rien}) &= \frac{1}{n}\cdot\frac{1}{n-1} \\
P(x \ \text{puis rien puis} \ y) &= \frac{1}{n}\cdot\frac{1}{n-2} \\
P(y \ \text{puis rien puis} \ x) &= \frac{1}{n}\cdot\frac{1}{n-2} \\
P(\text{rien puis} \ x \ \text{puis} \ y) &= \frac{1}{n - 1}\cdot\frac{1}{n-2} \\
P(\text{rien puis} \ y \ \text{puis} \ x) &= \frac{1}{n - 1}\cdot\frac{1}{n-2} \\
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
\mathbb{P}(c) &=
\binom{t}{k} k!\prod_{i = 0}^{k - 1}\frac{1}{n-i}\\
\prod_{i = 0}^{k - 1}n-i &= \frac{n!}{(n-k)!}\\
\text{d'ou}\quad k!\prod_{i = 0}^{k - 1}\frac{1}{n-i} &= \frac{k!(n-k)!}{n!} = \frac{1}{\binom{n}{k}}\\
\text{d'ou} \quad \mathbb{P}(c) &= \frac{\binom{t}{k}}{\binom{n}{k}}\\
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


