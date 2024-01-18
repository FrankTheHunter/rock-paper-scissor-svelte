<!-- Début du bloc script Svelte avec TypeScript -->
<script lang="ts">
  // Exporte les variables pour être utilisées dans ce composant Svelte
  export let userPicked: string = ""; // Choix de l'utilisateur (pierre, papier, ciseaux)
  export let machinePicked: string = ""; // Choix de la machine
  export let resultMessage: string; // Message indiquant le résultat du jeu
  export let onPlayagain: () => void; // Fonction pour rejouer, passée au composant
</script>

<!-- Structure HTML principale du jeu -->
<div class="game">
  <!-- Section affichant le choix de l'utilisateur -->
  <div>
    <p>You picked</p>
    <!-- Utilise la classe dynamique pour refléter le choix de l'utilisateur -->
    <div class="picked button-{userPicked}">
      <div class="circle">
        <!-- Image reflétant le choix de l'utilisateur -->
        <img src="./img/icon-{userPicked}.svg" alt={userPicked} />
      </div>
    </div>
  </div>

  <!-- Affiche le résultat du jeu si un message de résultat est présent -->
  {#if resultMessage}
    <div class="result">
      <!-- Texte du résultat du jeu -->
      <span id="resultText">{resultMessage}</span>
      <!-- Bouton pour rejouer, déclenche la fonction `onPlayagain` lorsqu'il est cliqué -->
      <button id="playagain" on:click={onPlayagain}>Play again</button>
    </div>
  {/if}

  <!-- Section affichant le choix de la machine -->
  <div>
    <p>The Machine picked</p>
    <!-- Utilise la classe dynamique pour refléter le choix de la machine -->
    <div class="picked button-{machinePicked}">
      <div class="circle">
        <!-- Image reflétant le choix de la machine -->
        <img src="./img/icon-{machinePicked}.svg" alt={machinePicked} />
      </div>
    </div>
  </div>
</div>

<!-- Styles CSS pour la mise en forme du jeu -->
<style>
  .game { /* Styles pour le conteneur principal du jeu */
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  .game div { /* Styles pour chaque division dans le jeu (choix de l'utilisateur et de la machine) */
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .game p { /* Styles pour les paragraphes indiquant les choix */
    font-size: 1.5rem;
    color: #fff;
    text-transform: uppercase;
  }

  .picked { /* Styles pour les éléments indiquant les choix effectués */
    display: flex;
    align-items: center;
    justify-content: center;
    border: none;
    border-radius: 50%;
    height: 300px;
    width: 300px;
    box-shadow: inset 0 -10px rgba(0, 0, 0, 0.15);
    margin: 50px;
  }

  .picked > div { /* Styles pour les cercles autour des images des choix */
    height: 220px;
    width: 220px;
    background: #fff;
    border-radius: 50%;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    box-shadow: inset 0 10px rgba(0, 0, 0, 0.15);
  }

  .game img { /* Styles pour les images représentant les choix */
    height: 120px;
    width: 120px;
  }

  .result > button { /* Styles pour le bouton "Play again" */
    width: 220px;
    height: 56px;
    color: hsl(349, 71%, 52%);
    text-transform: uppercase;
    font-family: "Barlow Semi Condensed", sans-serif;
    font-size: 1rem;
    letter-spacing: 2px;
    border-radius: 10px;
  }

  .result > span { /* Styles pour le texte du résultat du jeu */
    color: #fff;
    text-transform: uppercase;
    font-size: 3rem;
    letter-spacing: 2px;
    margin-bottom: 15px;
  }

  @media screen and (max-width: 575px) { /* Styles pour la mise en page responsive sur les petits écrans */
    .game > div {  /* Styles ajustés pour les divisions dans le jeu */
      display: flex;
      flex-direction: column-reverse;
    }

    .game p {  /* Styles ajustés pour les paragraphes sur les petits écrans */
      font-size: 1rem;
      color: #fff;
      text-transform: uppercase;
    }

    .picked { /* Styles ajustés pour les éléments des choix sur les petits écrans */
      height: 130px;
      width: 130px;
      margin: 20px;
    }

    .picked > div {  /* Styles ajustés pour les cercles autour des images des choix sur les petits écrans */
      height: 100px;
      width: 100px;
    }

    .game img { /* Styles ajustés pour les images des choix sur les petits écrans */
      height: 50px;
      width: 50px;
    }

    .result { /* Styles ajustés pour l'affichage du résultat sur les petits écrans */
      position: absolute;
      left: 0;
      right: 0;
      top: 380px;
    }
  }
</style>


