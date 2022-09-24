<template>
    <tr>
        <th>{{user.id}}</th>
        <td v-if="showInfo">{{user.nome}}</td>
        <td v-else><input type="text" placeholder="Nome" ref="nome" v-model="usuario.nome"/></td>
        <td v-if="showInfo">{{user.sobrenome}}</td>
        <td v-else><input type="text" placeholder="Sobrenome" v-model="usuario.sobrenome"/></td>
        <td v-if="showInfo">{{user.email}}</td>
        <td v-else><input type="email" placeholder="Email" v-model="usuario.email"/></td>
        <td v-if="showInfo">{{user.telefone}}</td>
        <td v-else><input type="tel" placeholder="Telefone" v-model="usuario.telefone"/></td>
        <td v-if="showInfo">{{user.cidade}}</td>
        <td v-else><input type="text" placeholder="Cidade" v-model="usuario.cidade"/></td>
        <td>
            <button @click="() => this.showInfo = !this.showInfo" v-if="showInfo" class="btn_one">Edit</button>
            <button @click="editUser" v-else class="btn_one">Confirmar</button>
            <button @click="$emit('deleteUser', user.id)" v-if="showInfo" class="btn_two">Del</button>  
            <button @click="cancelUser" v-else class="btn_two">Cancelar</button> 
        </td>
    </tr>
</template>

<script>

    export default {
        name: "UserData",
        emits: ["deleteUser"],
        props: {
            user: Object,
        },
        data() {
            return {
                showInfo: true,
                usuario: this.user,
                class: {
                    btnOne: 'btn_one',
                    btnTwo: 'btn_two',
                }
            }
        },
        created() {
            this.userBeforeEdit = { ...this.user }
        },
        methods: {
            editUser() {
                Object.assign(this.userBeforeEdit, this.user)
                this.showInfo = !this.showInfo
            },
            cancelUser() {
                Object.assign(this.user, this.userBeforeEdit)
                this.showInfo = !this.showInfo
            }
        }
    }
</script>

<style>
    td {
        font-size: 18px;
        padding: 15px 0;
    }
    button{
        padding: 10px 15px;
        margin: 05px 05px;
        text-transform: uppercase;
        cursor: pointer;
        font-weight: bold;
        border: none;
        border-radius: 5px;
    }
    .btn_one {
        background-color: rgb(252, 174, 28);
    }
    .btn_one:hover {
        background-color: rgba(252, 174, 28, 0.805);
    }
    .btn_two {
        background-color: rgb(241, 28, 28);
        color: white;
    }
    .btn_two:hover {
        background-color: rgb(248, 56, 56);
    }

    @media screen and (max-width: 900px) {
        th, td {
            display: block;
        }
    }
</style>