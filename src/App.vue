<template>
  <div>
    <h1>Hello Web</h1>
    <div>
   <!-- <div class="card-body products-detials" v-for="details in displayData" :key="details">
   <b>{{ details.id }}</b> -->
   <!-- <img :src="details.image"> -->
   <!-- <span>
   {{details.title}}
   </span>
    </div> -->
    </div>
    <!-- <div v-for="dataM in dataView" :key="dataM"> {{ dataM }} </div> -->
    <div>
    {{ mulplyArray}}
    {{ filterData }}
    </div>
    </div>
    
 
  <!-- <HelloWorld /> -->
</template>

<script>
import axios from 'axios';
// import HelloWorld from './components/HelloWorld.vue'

export default {
  // name: 'App',
  components: {
    // HelloWorld
  },
  data(){
    return{
     dataView: [],
     array: [2, 3, 4, 5, 6, 7],
     multiplier: 2,
     displayData: [],
     concatenated: [],
     filterData: [],

    };
    
  },
  methods:{
 async fetchApi() {
      try {
        const response = await axios.get('https://fakestoreapi.com/products');
        const data = response.data;
        this.dataView = data;
        console.log(data); // Do something with the fetched data
      } catch (error) {
        console.error('Error fetching API:', error);
      }
    },
     pushArray(){
     this.array.push(8);
     this.array.unshift();
    //  this.array.push(8);
    //  this.array.push(8);
    //  this.array.push(8);
    let array1 = [1, 2];
let array2 = [3, 4];
 this.concatenated = array1.concat(array2); 

 let filterArray = [1,2,3,4];
 this.filterData = filterArray.filter(num => num ===2);

    },
    
  async repeatApi(){
      let result =await axios.get('https://fakestoreapi.com/products');
      this.displayData = result.data;
      console.log( this.displayData);
    },

    postApi(){
      let postData = axios.post('https://fakestoreapi.com/products');
      console.log(postData);
    }
    
  },
   computed: {
    mulplyArray(){
      return this.array.map(num => num * this.multiplier);
    },
   
   
  },
  mounted() {
    this.fetchApi(); // Fetch the API when the component is mounted
    this.pushArray();
    this.repeatApi();
  },
}
</script>

<style>
.products-detials{
  position:relative;
  cursor: pointer;
  display: grid;
}
</style>
