<script>
  // Export de la fonction onclick pour qu'elle puisse être définie à l'extérieur de ce composant.
  export let onclick;

  // Export d'un tableau 'selectors', qui sera également défini à l'extérieur de ce composant.
  export let selectors = [];
</script>

<style>
  /* Style pour le conteneur principal '.choice'. */
  .choice {
    margin: 0 auto; /* Centrage horizontal. */
    display: flex; /* Utilisation de Flexbox pour le positionnement des boutons. */
    flex-wrap: wrap; /* Permet aux boutons de passer à la ligne si nécessaire. */
    justify-content: center; /* Centrage horizontal des éléments flex. */
    background: url("./img/bg-triangle.svg") no-repeat center; /* Arrière-plan avec image. */
  }

  /* Style pour les boutons '.buttons'. */
  .buttons {
    border: none; /* Pas de bordure. */
    border-radius: 50%; /* Forme circulaire. */
    height: 150px; /* Hauteur fixe. */
    width: 150px; /* Largeur fixe. */
    box-shadow: inset 0 -6px rgba(0, 0, 0, 0.15); /* Ombre interne pour un effet enfoncé. */
    margin: 50px; /* Marge autour de chaque bouton. */
    cursor: pointer; /* Curseur en forme de pointeur. */
  }

  /* Style pour le 'span' à l'intérieur des boutons. */
  .buttons > span {
    height: 120px; /* Hauteur fixe. */
    width: 120px; /* Largeur fixe. */
    background: #fff; /* Fond blanc. */
    border-radius: 50%; /* Forme circulaire. */
    display: inline-flex; /* Flexbox pour aligner l'image à l'intérieur. */
    align-items: center; /* Alignement vertical au centre. */
    justify-content: center; /* Alignement horizontal au centre. */
    box-shadow: inset 0 6px rgba(0, 0, 0, 0.15); /* Ombre interne. */
  }

  /* Styles adaptatifs pour les petits écrans. */
  @media screen and (max-width: 575px) {
    .buttons {
      /* Taille réduite pour les boutons sur les petits écrans. */
      height: 120px;
      width: 120px;
      margin: 20px;
    }

    .buttons > span {
      /* Taille réduite pour le 'span' sur les petits écrans. */
      height: 90px;
      width: 90px;
    }

    .choice {
      background-size: 210px; /* Ajustement de la taille de l'arrière-plan. */
    }
  }
</style>

<div class="choice">
  {#each selectors as name}
    <!-- Boucle sur chaque élément du tableau 'selectors'. -->
    <button class="buttons button-{name}" on:click={() => onclick(name)}>
      <!-- Bouton avec un style spécifique et un gestionnaire d'événements onclick. -->
      <span>
        <!-- Conteneur pour l'image du bouton. -->
        <img src="./img/icon-{name}.svg" alt={name} />
        <!-- Image dont la source dépend de l'élément 'name' du tableau 'selectors'. -->
      </span>
    </button>
  {/each}
</div>
