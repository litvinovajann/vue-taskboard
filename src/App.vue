<template>
  <div id="app">
    <div class="flex-container category-container">
    <taskCategory v-bind:key="category.id" v-bind:tasks="tasks" v-bind:category="category"
     v-for="category in categories">
    </taskCategory>
    </div>
    <div class="add-new-cat-container">
          <input v-model = "newColumnName" type="text"/>
          <button class="button-add-column" v-on:click="addCategory">Add Column</button>
    </div>
  <div id="task-detail"></div>
  </div>
  
</template>

<script>
import taskCategory from './components/Task-category.vue'
export default {
  name: 'App',
  components: {
    taskCategory
  },
 data: function() {return {
        categories: [
            { name: "backlog", id: "backlog" },
            { name: "progress", id: "progress" },
            { name: "done", id: "done" },
        ],
        tasks: [{
            name: "task1",
            type: "backlog"
        },
        {
            name: "task2",
            type: "done"
        }],
        categoryCounter: 0,
        newColumnName: '',
        taskCounter:0,
        newTaskName: ''
    }},
    methods: {
        addCategory: function() {
            let inputName = this.newColumnName;
            this.categories.push({name:inputName, id:inputName});
            this.newColumnName = '';
            this.categoryCounter++;
        },
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.flex-container {
    display: flex;
}
.category-container{
  height: 400px;
  overflow: auto;
  border: 1px solid #e6e6e6;
}
.add-new-cat-container {
  margin:4%;
}
</style>
