<template>
    <div>
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>

export default {
    name: "AddTodo",
    data: function(){
        return {
            title: ''
        }
    },
    methods: {
        addTodo: function(){
            const newTodo = {
                title: this.title,
                completed: false
            }
            // Send up to parent
            this.$emit('add-todo', newTodo);
            // Clear input field
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>