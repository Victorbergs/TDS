<template>
    <Header />
    <h1>Hello User, Welcome on update restaurant page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name" />
        <input type="text" name="address" placeholder="Enter address" v-model="restaurant.address" />
        <input type="text" name="contact" placeholder="Enter contact" v-model="restaurant.contact" />
        <button type="button" v-on:click="addRestaurant">Update restaurant</button>
    </form>
</template>
<script>
import Header from './Header.vue'
export default {
    name: 'Update-component',
    components: {
        Header
    },
    data() {
        return {
            restaurant: {
                name: '',
                address: '',
                contact: ''
            }
        }
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({ name: 'Signup' })
        }
    }
}
</script>