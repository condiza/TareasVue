<template>
    <form @submit.prevent="createTask" id="app">
        <label class="label" for="task">Nueva tarea: </label>
        <input type="text" v-model="newTask" id="task" class="input-task" placeholder="Escribe tu tarea aquí">
        <input type="submit" value="Crear tarea" class="submit-button">
        <ul>
            <li 
            v-for="(task, i) in tasks" 
            :key="'task' + i"
            :class="{completed: task.completed}"> 
            {{ task.text }}</li>
        </ul>
   </form>
</template>

<script>
export default {
    data() {
        return {
            newTask: "",
            tasks: [],
        };
    },
    methods: {
        createTask() {
            let task = {
                text: this.newTask,
                completed: false,
            };
            this.tasks.push(task);
            this.newTask = "";
            console.log(this.tasks);
        }
    }
};
</script>

<style scoped>
#app {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 20px;
}

.label {
    font-size: 18px;
    margin-bottom: 10px;
}

.input-task {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 300px;
    font-size: 16px;
    margin-bottom: 10px;
}

.submit-button {
    padding: 10px 15px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
}

.submit-button:hover {
    background-color: #218838;
}

.completed {
  text-decoration: line-through;
  color: grey;
}
</style>
