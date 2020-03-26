<template>
<!-- check if the class is condition is complete and if yes line through -->
<div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>{{todo.title}}</p>
</div>
    
</template>

<script>
export default {
    name: "TodoItem",
    props:["todo"]
}
</script>

<style scoped>
.todo-item{
    background: #f4f4f4;
    padding:10px;
    border-button:1px #ccc dotted;
}

.is-complete{
    text-decoration: line-through;
}

.del{
    background : #ff0000;
    color:#fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}
</style>