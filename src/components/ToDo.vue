<template>
    <div>
        <ul>
            <li v-for="(item, index) in todos" :key="index">
                {{item.title}}: {{item.desc}}
                <input type="checkbox" v-model="item.status" @change="$emit('compChange')"/>
                <button @click="$emit('delEntry', index)">X</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "ToDo",
    props: {
        todos: {
            type: Array
        },
    },
}
</script>

<style scoped>
    ul{
        list-style-type: none;
    }
</style>