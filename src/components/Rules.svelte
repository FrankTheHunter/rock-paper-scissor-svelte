<script>
  import { fly } from "svelte/transition"; // Importation de la transition 'fly' de Svelte.

  // Variable d'état pour gérer l'affichage du modal des règles.
  let isRuleOpen = false;

  // Fonction pour ouvrir le modal des règles. Déclenchée par le bouton "rules".
  function onRuleOpen() {
    isRuleOpen = true;
  }

  // Fonction pour fermer le modal des règles. Déclenchée par le bouton de fermeture dans le modal.
  function onClose() {
    isRuleOpen = false;
  }
</script>

<style>
  /* Style pour le bouton qui ouvre le modal des règles. */
  .button-rules {
    position: absolute; /* Position absolue pour le placement précis. */
    bottom: 5%;        /* Placé en bas à droite. */
    right: 5%;
    background: transparent; /* Fond transparent. */
    border: 2px solid hsl(217, 16%, 45%); /* Bordure personnalisée. */
    padding: 12px 36px; /* Espace interne du bouton. */
    border-radius: 10px; /* Coins arrondis. */
    text-transform: uppercase; /* Texte en majuscules. */
    color: #fff; /* Couleur du texte. */
    letter-spacing: 3px; /* Espacement des lettres. */
    font-size: 1.2rem; /* Taille de la police. */
    cursor: pointer; /* Curseur en forme de pointeur. */
  }

  /* Style pour le fond obscurci derrière le modal des règles. */
  .rules {
    display: flex; /* Utilisation de Flexbox pour le centrage. */
    position: fixed; /* Position fixe pour recouvrir toute la page. */
    top: 0;
    left: 0;
    width: 100vw; /* Largeur complète de la vue. */
    height: 100vh; /* Hauteur complète de la vue. */
    background: rgba(0, 0, 0, 0.6); /* Fond semi-transparent noir. */
  }

  /* Style pour le modal des règles. */
  .modal {
    position: absolute; /* Position absolue pour un alignement précis. */
    left: 40%;
    top: 10%; /* Centré verticalement. */
    background: #fff; /* Fond blanc pour le modal. */

    margin: 10% auto; /* Marge pour le centrage horizontal. */
    padding: 20px; /* Espace interne du modal. */
    width: 400px; /* Largeur fixe. */
    height: 400px; /* Hauteur fixe. */
    border-radius: 10px; /* Coins arrondis. */
  }

  /* Style pour les éléments à l'intérieur du modal. */
  .modal > div {
    display: flex; /* Utilisation de Flexbox pour l'alignement. */
    justify-content: space-between; /* Espacement entre les éléments. */
    align-items: center; /* Alignement vertical des éléments. */
    margin: 20px; /* Marge autour des éléments. */
  }

  /* Style pour le titre et le bouton de fermeture dans le modal. */
  .modal div span {
    text-transform: uppercase; /* Texte en majuscules. */
    font-size: 1.5rem; /* Taille de la police. */
    letter-spacing: 1px; /* Espacement des lettres. */
  }

  /* Style pour le bouton de fermeture dans le modal. */
  .modal div button {
    border: none; /* Pas de bordure. */
    background: transparent; /* Fond transparent. */
  }

  /* Styles adaptatifs pour les petits écrans. */
  @media screen and (max-width: 575px) {
    .button-rules {
      /* Ajustements pour le bouton sur petits écrans. */
      bottom: 30px;
      right: 120px;
      font-size: 0.8rem;
    }

    .modal {
      /* Ajustements pour le modal sur petits écrans. */
      padding: 0;
      width: 250px;
      height: 290px;
      margin: auto;
    }

    .modal > div {
      margin-top: 20px; /* Marge supérieure ajustée. */
    }

    .modal div span {
      font-size: 1rem; /* Taille de la police ajustée. */
    }

    .modal div:last-child img {
      width: 200px; /* Taille ajustée pour l'image. */
      height: 200px;
    }
  }
</style>

<div>
  <!-- Bouton pour ouvrir le modal des règles. -->
  <button class="button-rules" on:click={onRuleOpen}>rules</button>
</div>

{#if isRuleOpen}
  <!-- Contenu conditionnel pour afficher le modal des règles. -->
  <div class="rules" in:fly out:fly>
    <div class="modal">
      <div>
        <!-- Titre du modal et bouton de fermeture. -->
        <span>Rules</span>
        <button on:click={onClose}>
          <!-- Image du bouton de fermeture. -->
          <img src="./img/icon-close.svg" alt="close" />
        </button>
      </div>
      <div>
        <!-- Image illustrant les règles. -->
        <img src="./img/image-rules.svg" alt="rules" />
      </div>
    </div>
  </div>
{/if}
