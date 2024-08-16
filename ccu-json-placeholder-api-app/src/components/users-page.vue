<script>
import { ref } from 'vue';
export default {
    name: 'UsersPage',
    async setup() {
        const userList = ref(await fetch('https://jsonplaceholder.typicode.com/users').then(response => response.json()));
        console.log(userList);
    
        return { userList };
    },
    methods: {
        address(userAddress) {
            return `${userAddress.street}, ${userAddress.suite}, ${userAddress.city}, ${userAddress.zipcode}`
        }
    }
}</script>
<template>
    <div>
    <h1>Users</h1>
    <table>
        <thead>s
            <tr>
                <th>Id</th>
                <th>Name</th>
                <th>Username</th>
                <th>Email</th>
                <th>Address</th>
                <th>Phone</th>
                <th>Website</th>
                <th>Company</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for='(user, index) in this.userList' :key="`character-${index}`">
            <th>{{ user.id }}</th>
            <th>{{ user.name }}</th>
            <th>{{ user.username }}</th>
            <th>{{ user.email }}</th>
            <th>{{ address(user.address) }}</th>
            <th>{{ user.phone }}</th>
            <th>{{ user.website }}</th>
            <th>{{ user.company.name }}</th>
        </tr>
        </tbody>
    </table>
</div>
</template>
<style>
h1 {
    padding-block: 40px;
}

table {
    table-layout: fixed;
    width: 100%;
    border-collapse: collapse;
    border: 3px solid purple;
    background-color: #0b0a0b;
}

tbody tr:nth-child(odd) {
  background-color: #1f66d9;
}

tbody tr:nth-child(even) {
  background-color: #13ef76;
}

tbody tr {
  border: 3px solid purple;
}

thead th:nth-child(1) {
    width: 30%;
}
thead th {
    color: white;
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    padding: 20px;
    border-bottom: 3px solid purple;
}

thead th:nth-child(2) {
    width: 20%;
}

thead th:nth-child(3) {
    width: 15%;
}

thead th:nth-child(4) {
    width: 35%;
}

th,
td {
    padding: 20px;
}

</style>