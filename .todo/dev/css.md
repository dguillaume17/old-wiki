https://tympanus.net/codrops/
https://coryrylan.com/blog/how-to-center-in-css-with-css-grid

Centrer horizontalement
    Si on réduit trop trop un container flex centré, le texte se met sur plusieurs ligne et s'aligne sur la gauche.
    Il faut appliquer text-align: center;


centrer horizontalement et passer à la ligne les éléments qui "débordent"
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(70px, 1fr));
