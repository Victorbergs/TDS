<template>
    <h1>Hello User, Welcome to the home page</h1>
</template>
<script>
export default {
    name: 'Home-component',
       mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'Signup'})
        }
    }
}
</script>