<template>
    <form @submit="onSubmit">
        <div>
            <input type="text" placeholder="Nome" v-model="nome">
            <input type="text" placeholder="Sobrenome" v-model="sobrenome">
        </div>
        <div>
            <input type="email" placeholder="Email" v-model="email">
            <input type="tel" placeholder="Telefone" v-model="telefone">
        </div>
        <div>
            <input type="text" placeholder="Cidade" v-model="cidade">
            <button type="submit">Registrar</button>
        </div>
    </form>
</template>

<script>
    export default {
        name: 'FormComponent',
        emits: 'getInfo',
        data() {
            return {
                id: parseInt('1'),
                nome: '',
                sobrenome: '',
                email: '',
                telefone: '',
                cidade: '',
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault()

                const usuario = {
                    id: this.id,
                    nome: this.nome,
                    sobrenome: this.sobrenome,
                    email: this.email,
                    telefone: this.telefone,
                    cidade: this.cidade
                }

                this.$emit('getInfo', usuario);

                this.id = usuario.id + 1
                this.nome = '';
                this.sobrenome = '';
                this.email = '';
                this.telefone = '';
                this.cidade = '';
            }
        }
    }
</script>

<style scoped>
    form {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
    }
    input {
        display: block;
        margin-top: 10px;
        margin-right: 10px;
        border-radius: 8px;
        padding: 10px 0;
        padding-left: 20px;
        width: 280px;
        border: 1px solid grey;
    }
    button {
        padding: 10px;
        width: 300px;
        margin-top: 10px;
        margin-left: 0px;
        border: none;
        border-radius: 8px;
        font-size: 16px;
        font-weight: bold;
        text-transform: uppercase;
        background-color: rgb(252, 174, 28);
        color: white;
        cursor: pointer;
    }
    button:hover {
        background-color: rgba(252, 174, 28, 0.725);
    }
</style>