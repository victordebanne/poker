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
$$
