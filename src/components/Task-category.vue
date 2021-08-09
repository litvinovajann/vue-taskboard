 <template>
 <div class='task-category'>
            <div class='cat-header'>{{category.name}}</div>
            <div class="tasks">
                <Task v-bind:key="task.type"
                 v-bind:task = "task"
                 v-for="task in filterTasks(tasks, category.id)">
                    {{task.name}}
                 </Task>
            </div>
            <input v-model="newTaskName" type="text"/>
            <button class="button-add-column" v-on:click="addTask(category.name)">Add task</button>
</div>
</template>

<script>
import Task from './Task.vue'
export default {
    name:"TaskCategory",
    props: ["category", "tasks"],
    data: function() {
        return {
            newTaskName: ''
        }
    },
     methods: {
        filterTasks: function(tasks,neededType) {
            return tasks.filter(function(task){
                return task.type == neededType;
            })
        },
         addTask : function(type) {
            let inputName = this.newTaskName;
            this.tasks.push({name:inputName, type:type})
            this.newTaskName = '';
            this.taskCounter++;
           
        }
    },
    components: {Task}
}
</script>

<style scoped>
 .cat-header{
     margin:2%;
     font-weight: 600;
     text-transform: capitalize;
 }
.task-category {
    width:25%;
    margin:2%;
    border: 0.5px solid #e6e6e6;
}
.tasks{
    height: 300px;
}
</style>