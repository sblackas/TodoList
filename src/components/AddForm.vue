<template>
  <b-form inline class="formulaire">
        
    <b-input-group prepend="New Task" class="mb-2 mr-sm-2 mb-sm-0">
      <b-input id="inline-form-input-username" placeholder="todo name" type="text" v-model="newTask"></b-input>
    </b-input-group>
    <b-button v-on:click="addTask">Add</b-button>
  </b-form>

<!-- Ne pas oublier de v-model="newtask" autrement il est initialisé dans data return mais pas appelé ni lié à l'input
On le met dans l'input car c'est à cet endroit que sera entrée la nouvelle tâche
 -->

</template>


<script>
export default {
    name : 'AddForm',
    data (){
    return {
        newTask: ""
    }
},
        methods: {
        addTask() {
            // console.log(this.task.name)
            this.$parent.$emit('addTodo', this.newTask)
            this.newTask=""
        }
    }
}
    
</script>

<!-- $parent permet d'envoyer l'évènement directement au composant parent(App.vue) sans passer par le père de AddForm qui est MyJumbotron.vue $parent envoie l'évènement à la place de MyJumbotron -->


<style>

.formulaire {
justify-content: center;
}

</style>