<template>
<div>
  <header>
          <h1>Shuffle and Sort </h1>
          </header>
<div class = "container">
    <div class = "col bigitem" >
    <div class="cards" v-if="sorted" >
      <div class="card" 
      v-bind:style="{backgroundColor: colors[i]}"
      :key="i"
       v-for="(item,i) in items" >{{ item }}</div>
    </div>
    <div class="cards" v-if="shuffled">
      <div class="card"
      v-bind:style="{backgroundColor: colors[j]}"
      :key="j"
       v-for="(i,j) in shuffledArray">{{ i }}</div>
    </div>
  </div>
<div class = "col smallitem">
      <div id="databinding  ">
      <div class = "row flex">
      <div class = "col">
        <button class = "button" @click="shuffle()">Shuffle</button>
      </div>
      <div class = "col">
        <button class = "button"   @click="sort()">Sort</button>
      </div>
      </div>
    </div>
</div>
    </div>
  
      <footer>
        <h1>Shuffle and sort by Puja Gupta</h1>
        <div>
          <span>
         <img alt="logo maersk" class ="ig" src="../assets/maersk.png"></span>
       </div>
  </footer>
    </div>
</template>

<script>
 import image from "../assets/maersk.png"
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      image: image,
      items: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      shuffledArray: null,
      sorted: true,
      shuffled: false,
      colors:[
       "#000000",
       "#2BBEAD",
        "#333333",
        "6F98AB",
        "#FFFFF",
        "#BFBFBF",
        "#EFEFEF",
        "#2BBEAD",
        "#72C3DC",
        ]
      
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
  background-color: grey;
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
.button {
  background-color:dodgerblue;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  /*grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));*/
}
.bigitem {
   /* This will be twice as */
   /* big as the small item. 
  *flex: 2 0 0;*/
  width:75%;

  }
.smallitem {
  *flex: 1 0 0;
}
.container {
  display: flex; /* or inline-flex */
   flex-wrap: wrap-reverse 
}
.bt{
  display: flex; /* or inline-flex */
  flex-direction:column-reverse;

} 

.bttn{
   display: flex; /* or inline-flex */
  flex-direction:column-reverse;

}
.wrapper--accessibility-tools {
  display: flex;
  flex-wrap: wrap;
} 
.fr{
  float: left;
}
@media only screen and (max-width: 600px) {
.flex{
   display: flex;
}
}
.xy {
width: 6em;
}

.ig{
  width: 7%;
    /* float: left; */
    display: flex;
    flex-wrap: wrap-reverse;
}

</style>
