<template>
  <div>
    <div id="databinding">
      <span>
        <button @click="shuffle()">Shuffle</button>
      </span>
      <span></span>
      <span>
        <button @click="sort()">Sort</button>
      </span>
    </div>
    <div class="cards" v-if="sorted">
      <div class="card" v-for="item in items" :key="item.id">{{ item }}</div>
    </div>
    <div class="cards" v-if="shuffled">
      <div class="card" v-for="i in shuffledArray" :key="i.id">{{ i }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      items: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      shuffledArray: null,
      sorted: true,
      shuffled: false
    };
  },
  methods: {
    shuffle() {
      this.shuffled = true;
      this.sorted = false;
      let items = [...this.items];
      let first,
        second,
        temp,
        count = items.length;
      for (let i = 0; i < 10; i++) {
        first = Math.floor(Math.random() * count);
        second = Math.floor(Math.random() * count);
        temp = items[first];
        items[first] = items[second];
        items[second] = temp;
      }
      this.shuffledArray = items;
    },
    sort() {
      this.shuffled = false;
      this.sorted = true;
      //let items = [...this.items];
      let items = [...this.shuffledArray];
      //return items.sort();
      //this.shuffle = false;
      //return items;
      this.items = items.sort();
    }
  },
  mounted() {
    this.sort();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
html {
  font-size: 22px;
}
body {
  padding: 1rem;
}

.card {
  background-color: dodgerblue;
  color: white;
  padding: 1rem;
  height: 4rem;
}

.cards {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-gap: 1rem;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}
</style>
