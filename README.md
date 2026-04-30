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

### probabilité du tirage d'une combinaison c parmi n cartes sachant les cartes sans remise

$$
\mathbb{P}(c | E) = \mathbb{P}(c - c \cap E) 
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


