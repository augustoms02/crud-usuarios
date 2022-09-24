<template>
  <div>
    <h1>Crud - Usuários </h1>
    <FormComponent @getInfo = "showInfo"/>
    <UserList :data="usuarios"/>
  </div>
</template>

<script>
import FormComponent from './components/FormComponent.vue';
import UserList from './components/UserList.vue';

  export default {
    name: "App",
    components: { FormComponent, UserList },
    data() {
            return {
                usuarios: [
                  {
                    id: 0,
                    nome: 'Augusto', 
                    sobrenome: 'Maldonado', 
                    email: 'augustoms02@hotmail.com',
                    telefone: '34997341871',
                    cidade: 'Uberlândia'
                  }
                ]
            }
        },
    methods: {
      showInfo(usuario) {
        this.usuarios.push(usuario)
      },
    }
}
</script>

<style scoped>
  h1 {  
    width: 100%;
    text-align: center;
    text-transform: uppercase;
  }
</style>