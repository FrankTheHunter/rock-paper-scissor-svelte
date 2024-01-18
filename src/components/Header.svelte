<script lang="ts">
  // Exporte une variable `score` de type nombre, qui sera passée par le parent de ce composant.
  export let score: number;
</script>

<div class="header-game">
  <div class="header-game-name">
    <!-- Affiche le titre du jeu -->
    <h1>Rock Paper Scissors</h1>
  </div>
  <div class="header-game-score">
    <!-- Affiche le score actuel. Si `score` n'est pas fourni, affiche un trait (-). -->
    <span>Score</span>
    <p>{score || '-'}</p>
  </div>
</div>

<style>
  
  .header-game {
    /* Style du conteneur principal : bordure, coins arrondis, largeur spécifique, alignement horizontal des enfants */
    border: 2px solid hsl(217, 16%, 45%);
    border-radius: 20px;
    width: 700px;
    display: flex;
    justify-content: space-between;
    margin: 50px 0;
  }

  .header-game-name {
    /* Style pour le titre du jeu : marges, couleur, police de caractères, transformation du texte */
    margin: 20px 30px;
    color: #fff;
    font-family: "Barlow Semi Condensed", sans-serif;
    width: 160px;
    text-transform: uppercase;
    line-height: 0.8;
    font-size: 1.5rem;
  }

  .header-game-score {
    /* Style pour l'affichage du score : padding, alignement du texte, arrière-plan, bordures arrondies */
    padding: 10px 30px;
    text-align: center;
    margin: 16px 20px;
    background: #fff;
    width: 150px;
    border-radius: 10px;
  }

  .header-game-score span {
    /* Style pour l'étiquette 'Score' : transformation du texte, taille de la police, couleur, espacement des lettres */
    text-transform: uppercase;
    font-size: 1.2rem;
    color: hsl(229, 64%, 46%);
    letter-spacing: 2px;
  }

  .header-game-score p {
    /* Style pour le nombre de points : taille de la police, poids de la police, couleur */
    font-size: 4rem;
    font-weight: 700;
    color: hsl(229, 25%, 31%);
  }

  @media screen and (max-width: 575px) {
    /* Query pour les écrans de petite taille (moins de 575px de largeur) */
    .header-game {
      /* Ajuste le style du conteneur principal pour les petits écrans */
      border: 1px solid hsl(217, 16%, 45%);
      width: 315px;
      margin: 26px;
    }

    .header-game-name {
      /* Ajuste le style du titre pour les petits écrans */
      line-height: 0.8;
      font-size: 12px;
      font-weight: 500;
      width: 20px;
    }

    .header-game-score {
      /* Ajuste le style de l'affichage du score pour les petits écrans */
      background: #fff;
      width: 78px;
    }

    .header-game-score span {
      /* Ajuste le style de l'étiquette 'Score' pour les petits écrans */
      display: flex;
      justify-content: center;
      text-align: center;
      font-size: 0.5rem;
    }

    .header-game-score p {
      /* Ajuste le style du nombre de points pour les petits écrans */
      font-size: 2rem;
      font-weight: 700;
    }
  }
</style>
