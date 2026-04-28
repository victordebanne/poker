# poker

## calcul de la probabilité d'avoir la meilleure main sachant les cartes. 

$$
\begin{align}
&\mathbb{P} (\text{gagner} | \text{cartes}) = 
\sum_{i = 0}^N \mathbb{P}(c_i \ \text{gagnant}) \cdot \mathbb{P}(c_i | \text{cartes}) \\
&\text{avec c les différentes combinaisons possibles (paire, carré, couleur...)}
\end{align}
$$

la probabilité de tirer une carte $x$ sachant les cartes (cartes du joueur et cartes sur le plateau) : 

$$
\begin{align}
\text{avec} \quad E \quad \text{l'ensemble des cartes connues} \\
\text{et} \quad F \quad \text{l'ensemble des cartes non connues.}\\
\mathbb{P}(x) =
\begin{cases}
\frac{1}{52 - \lvert E \rvert} \quad \text{si} \quad x \notin E \\
0 \quad \text{sinon}
\end{cases}
\end{align}
$$
