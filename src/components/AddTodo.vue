<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data(){
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            console.log("Submit", this.title)
            if (this.title.trim()){
                const newToto = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newToto)
                this.title = ''
            }
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        justify-content: center;
    }

    input {
        width: 400px;
    }
</style>