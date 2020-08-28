<template>
    <ul>
        <SingleTodo v-for="element in list" v-bind:key="element.id" v-bind:task="element"  v-on:completed="toggle"/>
    </ul>
 
<!-- Boucle v-for in : j'itère à travers chaque éléments de ma liste, -->
<!-- v-bind:key va nous servir à attribuer une clé unique à chaque élément de ma liste pour un rendu de la liste plus efficient, on prend l'id puisque celui est unique -->
<!-- v-bind:task="element" mon élément s'appelle task désormais -->

</template>

<script>
import SingleTodo from './SingleTodo.vue'
export default {
    name: 'LisTodo',
    components: {
        SingleTodo
    },
    props:['list'],
    methods : {
        toggle(id){
            // console.log("J'ai detecté un event")
            this.$emit('completed', id)
        }
    }

}
</script>
