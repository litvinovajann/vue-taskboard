<template>
  <div id="app">
    <div class="flex-container category-container">
    <taskCategory v-bind:key="category.id" v-bind:tasks="tasks" v-bind:category="category"
     v-for="category in categories">
    </taskCategory>
    </div>
    <div class="add-new-cat-container">
          <label for="columName">put your column name here </label>
          <input v-model = "newColumnName" name="columnName" type="text"/>
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
        taskTypes: [{
          name: "new functionality",
          code: "feat"
        },{
          name: "defect",
          code: "defect"
        },{
          name: "tech duty",
          code: "tech"
        },],
        categories: [
            { name: "backlog", id: "backlog" },
            { name: "progress", id: "progress" },
            { name: "done", id: "done" },
        ],
        tasks: [{
            name: "task1",
            type: "backlog",
            author: "Somebody",
            createDate: new Date(),
            performer: "Somebody 2",
            taskType: "feat",
            points: 2,
            description: "description of the first task"

        },
        {
            name: "task2",
            type: "done",
            author: "Somebody3",
            createDate: new Date(),
            performer: "Somebody 4",
            taskType: "tech",
            points: 1,
            description: "description of the second task"
        }],
        categoryCounter: 0,
        newColumnName: '',
        taskCounter:0,
        newTaskName: ''
    }},
  provide: function() {
    return {tasks: this.tasks, validator: this.validator}
    },
    methods: {
        validator: function(input) {
          if (input.length > 0) {
            return true;
          }
          return false;
        },
        addCategory: function() {
            let inputName = this.newColumnName;
            if (this.validator(inputName)){
            this.categories.push({name:inputName, id:inputName});
            this.newColumnName = '';
            this.categoryCounter++;
            } else {
              alert('data incorrect')
            }
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
