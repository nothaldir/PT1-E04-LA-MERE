<template>
  <div class="timeline">
    <h3>
      Votre enfant a:<br>
      <strong>{{ age }}</strong>
    </h3>
    <div class="bars">
      <div class="bar" v-for="n in length">
        <div class="line" :class="[n > count ? '' : 'active']"></div>
      </div>
    </div>
    <router-link class="link" to="/reveal">
      <h3>PASSER<br>L'EXPERIENCE</h3>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'timeline',
  props: ['length', 'count', 'age'],
  data: () => ({
    tempAge: '3 mois',
  }),
  methods: {
    changeChapter(n) {
      this.$store.commit('changeChapter', { n })
    },
  },
}
</script>

<style lang="scss" scoped>
  @import '../variables.scss';
  .timeline {
    background-color: black;
    width: 100vw;
    display: flex;
    flex-flow: row wrap;
  }
  h3 {
    color: white;
    margin: .5rem 1rem;
    text-align: center;
    strong {
      font-size: 2rem;
    }
  }
  .bars {
    display: flex;
    flex-flow: row nowrap;
    flex-grow: 1;
    justify-content: space-between;
    align-items: center;
    margin: 0 auto;
    flex-grow: 1;
    max-width: 60rem;
  }
  .bar {
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100%;
    margin: 0 .3rem;
    flex-grow: 1;
  }
  .line {
    background-color: #393939;
    height: .2rem;
    transition: all .2s ease-out;
  }
  .active {
    background-color: white;
  }

</style>
