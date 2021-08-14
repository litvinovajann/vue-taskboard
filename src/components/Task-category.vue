 <template>
 <div class='task-category'>
            <div class='cat-header'>{{category.name}}</div>
            <div class="tasks">
                <Task v-bind:key="task.type"
                 v-for="task in filterTasks(tasks, category.id)"   
                 v-bind:task = "task">
                    {{task.name}}
                 </Task>
            </div>
            <input class="input-add-task" v-model="newTaskName" type="text"/>
            <button class="button-add-column" v-on:click="addTask(category.name)">Add task</button>
</div>
</template>

<script>
import Task from './Task.vue'
export default {
    name:"TaskCategory",
    props: ["category"],
    inject: ["tasks", "validator"],
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
            if(this.validator(inputName)) {
            this.tasks.push({name:inputName, type:type})
            this.newTaskName = '';
            this.taskCounter++;
            }
            else alert('empty task')
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

.input-add-task {
    max-width: 80%;
    margin: 0 auto;
}

</style>