<template>
  <div id="discover-measures">
    <h4>Les mesures phares de la loi EGAlim en restauration collective</h4>
    <h5>
      Découvrez les mesures, leurs échéances,
      le public cible ainsi que des ressources pour vous aider à atteindre leurs objectifs.
    </h5>
    <ol id="measures-list">
      <router-link
        v-for="measure in keyMeasures"
        :key="measure.id"
        :to="{ name: 'KeyMeasurePage', params: { id: measure.id } }"
        class="measure-link"
      >
        <li class="measure-item">
          <p class="measure-title"><KeyMeasureTitle :measure="measure"/></p>
          <p class="discover-measure">→ En savoir plus</p>
        </li>
      </router-link>
    </ol>
    <a id="download-documentation" download href="">
      Télécharger la documentation complète
    </a>
  </div>
</template>

<script>
  import KeyMeasureTitle from "@/components/KeyMeasureTitle";
  import keyMeasures from "@/data/key-measures.json";

  export default {
    components: {
      KeyMeasureTitle
    },
    data() {
      return {
        keyMeasures,
      };
    },
  }
</script>

<style scoped lang="scss">
  #discover-measures {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 70px 0;
  }

  #discover-measures > h4 {
    font-weight: bold;
    font-size: 37px;
    text-align: center;
    color: $orange;
    margin: 0.8em 0;
  }

  #discover-measures > h5 {
    font-size: 22px;
    text-align: center;
    color: $light-grey;
    max-width: 30em;
    margin: 0.5px 0;
  }

  #measures-list {
    padding: 0;
    margin: 5em 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    list-style: none;
  }

  a.measure-link {
    text-decoration: none;
    margin: 0.5em 0.7em;
  }

  .measure-item {
    border: 1px solid $light-yellow;
    background: $light-yellow;
    border-radius: 22px;
    height: 10em;
    width: 10em;
    border-radius: 22px;
    padding: 2em 1em;
    text-align: left;
    position: relative;
    transition: all ease .25s;
  }

  .measure-item:hover {
    border-color: $orange;
    transform: scale(1.02);
  }

  div.measure-text {
    height: 100%;
  }

  p.measure-title {
    font-weight: bold;
    font-size: 16px;
    color: $grey;
    margin: 0;
  }

  p.discover-measure {
    position: absolute;
    bottom: 2em;

    font-size: 16px;
    color: $grey;
  }

  #download-documentation {
    width: 423px;
    border-radius: 50px;
    background: $orange;
    padding: 1em 0;

    text-decoration: none;
    font-weight: bold;
    font-size: 18px;
    line-height: 23px;
    text-align: center;
    color: $white;

    /* TODO: supprimer quand on a le lien */
    display: none;
  }
</style>
