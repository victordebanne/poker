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
\mathbb{P}(x) =
\begin{cases}
\frac{1}{52 - \lvert E \rvert} \quad \text{si} \quad x \notin E \\
1 \quad \text{sinon}
\end{cases}
\end{align}
$$

on peut calculer la probabilité de chaque combinaison, à chaque tour, ainsi :

$$
\mathbb{P}(c_i | E) = \prod_{k = 1}^{K} \mathbb{P} (x_k)
$$

$$
\text{avec} \quad K \quad \text{le nombre de cartes dans la combinaison et} \quad x_k \quad \text{la carte de la combinaison}
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
