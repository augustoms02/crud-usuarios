<template>
    <table>
        <tr>
            <th>ID:</th>
            <th>Nome:</th>
            <th>Sobrenome:</th>
            <th>Email:</th>
            <th>Telefone:</th>
            <th>Cidade:</th>
            <th></th>
        </tr>
        <UserData v-for="user in data" :key="user.id" :user="user" @deleteUser = "deleteUser"/> 
    </table>
</template>

<script>
    import UserData from './UserData.vue';

    export default {
    name: "UserList",
    props: {
        data: Array,
    },
    data() {
        return {
            users: this.data,
        }
    },
    components: { UserData },
    methods: {
        deleteUser(id) {
            const indexFound = this.users.findIndex((obj) => obj.id === id);
            this.users.splice(indexFound, 1); 
        }
    }
}
</script>

<style scoped>
    table {
        text-align: center;
        border-collapse: collapse;
        margin: 100px auto;
        border: none;
        width: 80%;
    }
    th {
        width: 10%;
        text-transform: uppercase;
        font-weight: bold;
        padding: 20px;
    }
    tr {
        border-top: 2px solid lightgray;
        border-bottom: 1px solid lightgray;
    }
    tr:nth-child(odd) {
        background-color: none;
    }
    tr:nth-child(even) {
        background-color: rgba(211, 211, 211, 0.337);
    }

    @media screen and (max-width: 900px) {
        th {
            display: none
        }
    }

</style>