<template>
    <Header />
    <h1>Hello {{ name }}, Welcome to the home page</h1>
    <div class="table-container">
        <table border="1">
            <tr>
                <td>Id</td>
                <td>Name</td>
                <td>Contact</td>
                <td>Address</td>
                <td>Actions</td>
            </tr>
            <tr v-for="item in restaurant" :key="item.id">
                <td>{{ item.id }}</td>
                <td>{{ item.name }}</td>
                <td>{{ item.contact }}</td>
                <td>{{ item.address }}</td>
                <td><router-link :to="'/update/'+item.id">Update</router-link></td>

            </tr>
        </table>
    </div>
</template>
<script>
import Header from './Header.vue'
import axios from 'axios';
export default {
    name: 'Home-component',
    data() {
        return {
            name: '',
            restaurant: []
        }
    },
    components: {
        Header
    },
    async mounted() {
        let user = localStorage.getItem('user-info');
        this.name = JSON.parse(user).name;
        if (!user) {
            this.$router.push({ name: 'Signup' })
        }
        let result = await axios.get('http://localhost:3000/restaurant');
        console.warn(result)
        this.restaurant = result.data;
    }
}
</script>

<style>
td {
    width: 160px;
    height: 40px;
}

.table-container {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>