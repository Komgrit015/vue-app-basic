<script setup>
import MyBar from './components/MyBar.vue';
import MyCard from './components/MyCard.vue';

</script>

<template>
  <header>
    <MyBar/>
  </header>

  <main>
    <h1 style="padding-left: 10px">Attractions</h1>
    <div className="grid-container">
    <MyCard v-for="item in items " v-bind="item" />
    </div>
  </main>
</template>
<script>
  export default {
    data() {
      return {
        items: []
      }
    },
    created() {
      fetch('https://www.melivecode.com/api/attractions/')
      .then(res => res.json())
      .then((result) => {
        this.items = result
      })
    }
  }
</script>
<style scoped>
.grid-container {
  display: grid;
  grid-column-gap: 0.5rem;
  grid-row-gap: 0.5rem;
}
@media (min-width: 576px) {
  .grid-container { grid-template-columns: repeat(1, 1fr); }
}
@media (min-width: 992px) {
  .grid-container { grid-template-columns: repeat(3, 1fr); }
}
</style>
