<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{index+1}}</strong>
            {{todo.title | upperCase}}
        </span>
        <button class="rm" 
            v-on:click="$emit('remove-todo', todo.id)"
        >&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            reqired: true
        },
        index: Number
    },
    filters: {
        upperCase(value) {
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
    }
    .rm {
        background: rgb(55, 228, 185);
        color: #fff;
        border-radius: 50%;
        font-weight: bold;
    }
    input {
        width: 1.3em;
        height: 1.3em;
        margin-right: 2rem;
        background-color: white;
        border-radius: 20%;
        vertical-align: middle;
        border: 1px solid rgb(64, 201, 255);
        cursor: pointer;
    }
    .done {
        text-decoration: line-through;
    }
</style>