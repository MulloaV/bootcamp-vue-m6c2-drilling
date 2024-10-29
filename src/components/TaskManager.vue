<template>
    <div class="task-manager">
        <h1>Lista de tareas</h1>
        <input class="input" type="text" v-model="newTask" placeholder="Añadir nueva tarea" />
        <button class="btn" @click="addTask">Añadir</button>
        <ul>
            <li v-for="(task, index) in tasks" :key="index">
                {{ task }}
                <button @click="editByIndex(index)">Editar</button>
                <button @click="deleteByIndex(index)">Borrar</button>
            </li>
        </ul>
    </div>
</template>

<script>
import Vue from 'vue';

export default Vue.extend({
    name: 'TaskManager',
    data() {
        return {
            tasks: [], 
            newTask: '',
            editIndex: null 
        };
    },
    methods: {
        addTask() {
            if (this.newTask.trim() !== '') {
                if (this.editIndex !== null) {
              
                    this.tasks.splice(this.editIndex, 1, this.newTask);
                    this.editIndex = null;
                } else {

                    this.tasks.push(this.newTask);
                }
                this.newTask = ''; 
            }
        },
        editByIndex(index) {
           
            this.newTask = this.tasks[index];
            this.editIndex = index;
        },
        deleteByIndex(index) {
          
            this.tasks.splice(index, 1);
        }
    }
});
</script>

<style>
.task-manager {
    max-width: 600px;
    margin: 0 auto;
    padding: 30px;
    background-color: #ebee4bbe;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    font-size:larger;
    text-align: center
}
.btn {
    background-color: #4CAF50;
    color: white;
    border: none;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
}
.input {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
    margin-bottom: 10px;
}
</style>