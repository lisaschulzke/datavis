<template>
  <div>
    <div>
    Date Start<input type="range" min="0" :max="asteroids.length" v-model="rangeMin" id="rangeStart">
    Date End<input type="range" min="0" :max="asteroids.length" v-model="rangeMax" id="rangeEnd">
    Max Mass<input type="range" min="0" :max="1000000000000000" v-model="rangeMax" id="massMax">
    </div>
    <!-- key muss property von asteroids beinhalten, was immer gleich ist überall -->
    <div class = "asteroid" v-for="a in rangeOfAsteroids" :key="a.name" :style="{ width: Math.sqrt(a.mass/10) + 'px', height: Math.sqrt(a.mass/10) + 'px' }">
    </div>
  </div>
</template>

<script>
import mydata from "../assets/data.json"


export default {
  data() {
    return {
      //new component generated which is filled from the mydata from the data.json
      asteroids: [],
      rangeMin: 0,
      rangeMax: 1000,
      massMax: 1000000000000000,
    }
    },
  mounted(){
    console.log(mydata[0]);
    //looks for all the objects in the array, if one´s mass is 0 or undefined
    for (let i = 0; i < mydata.length; i++){
      const element = mydata[i];
      if (element.mass === 0 || element.mass === undefined){
        // if so, mass is set to 1
        element.mass = 1;
      }
    } mydata.sort(function(x,y){
        // if(x.year > y.year) return 1
        // else return 0
        x.year > y.year ? 1:0
    })
    this.asteroids = mydata;
  },
  // computed is like property and function at the same time but advantage is auto act. data
  computed: {
    rangeOfAsteroids: function(){
      return this.asteroids.slice(this.rangeMin, this.rangeMax)
    },
    asteroidsBelowMaxMass: function(){
      return this.asteroids.filter(function(x){
        // x is placeholder for an asteroid element
        return x.mass < this.massMax
      })
    }
  }
  }

</script>

<style>
  .asteroid {
    background-color: grey;
    border: 1px solid black;
    display: inline-block;
    border-radius: 50%;
  }
</style>