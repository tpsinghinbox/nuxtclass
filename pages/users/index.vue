<template>
<div>
  <h3>{{title}}</h3>
  <ul>    
    <li v-for="xxx in users" :key="xxx.id">
        <NuxtLink :to="'/users/'+xxx.id">{{xxx.name+'-('+xxx.address.city+')'}}</NuxtLink>
    </li>
  </ul>
  </div>
  
</template>

<script>
import axios from 'axios'
export default {  
  data(){
    return{
      title:'This is user page',
      users:[]
    }
  },
  async fetch(){
      await this.getusers()
  },
  methods:{
    async getusers(){
      const allusers = await axios.get('https://jsonplaceholder.typicode.com/users')  
      this.users = allusers.data
      
    }
  }
  // created(){
  //    fetch('https://jsonplaceholder.typicode.com/users')
  //     .then(response => response.json())
  //     .then(json => {
  //         console.log(json)
  //         this.users = json
  //     })
  // }
}
</script>

<style>

</style>