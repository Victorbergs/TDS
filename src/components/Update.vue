<template>
    <Header />
        <h1>Hello User, Welcome on update restaurant page</h1>
    </template>
    <script>
    import Header from './Header.vue'
    export default {
        name: 'Update-component',
        components:{
            Header
        },
           mounted(){
            let user = localStorage.getItem('user-info');
            if(!user){
                this.$router.push({name:'Signup'})
            }
        }
    }
    </script>