<template>
    <div>
        <p>{{title}}</p>
       <h1>Hello User {{userdata.name}}</h1>
       <p>{{userdata.email}}</p>
        <p>{{userdata.phone}}</p>
        <p>https://insomnia.rest/</p>
        <NuxtLink to="/users">User</NuxtLink>
    </div>
</template>



<script>
export default {
    data(){
        return{
            title:"user data",
            userdata : []
        }
    },
    created(){
        fetch(`https://jsonplaceholder.typicode.com/users/${this.$route.params.id }`)
        .then(response => response.json())
        .then(json => {
            this.userdata = json
        })
    },
}
</script>



<style>

</style>