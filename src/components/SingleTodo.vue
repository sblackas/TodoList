<template>
    <li v-on:click="toggle" v-if="task.todo == false" class="completed">
        <b-icon icon="check-circle-fill"></b-icon>{{task.name}}
    </li>
        <li v-on:click="toggle" v-else-if="task.todo == true">
        <b-icon icon="check2-circle"></b-icon>{{task.name}}
    </li>
    <!-- le v-on:click permet de recuperer l'évènement click à la fonction toggle qu'on $emit aux parents ensuite -->
</template>

<!-- dans le v-on:click j'aurais pu mettre "toggle(task.id)" et dans la method faire : 
    methods: {
        toggle(id) {
            // console.log(this.task.name)
            this.$emit('completed',id)
        }
    }

    Etant donné que je l'ai déjà indiqué dans le v-on. Dans methods des parents ca va automatiquement detecté id et le mettre dans les parametres
 -->

<script>
export default {
    name: 'SingleTodo',
    props:['task'],
    methods: {
        toggle() {
            // console.log(this.task.name)
            this.$emit('completed', this.task.id)
        }
    }
}
</script>



<style>
li {
    list-style-type: none;
}

.completed {
 text-decoration: line-through;
}

</style>