<template>
    <form ref="form">
        <h2>New Task</h2>
        <label for="taskTitle">title</label>
        <input type="text" name="taskTitle" v-model="title" id="taskTitle">
        <label for="taskDesc">description</label>
        <input type="text" name="taskDesc" v-model="desc" id="taskDesc">
         <button @click="submitActions">Submit</button>
    </form>
</template>

<script>
export default {
    name: "TaskForm",
    data() {
        return {
            title: "",
            desc: ""
        }
    },
    props: {
        todos: {
            type: Array
        },
    },
    methods: {
        submitActions(e) {
            e.preventDefault();
            this.todos.push({title:this.title, desc:this.desc,status:false})
        },
    },
}
</script>

<style>

</style>