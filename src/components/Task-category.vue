 <template>
 <div class='task-category'>
            <div class='cat-header'>{{category.name}}</div>
            <div class="tasks">
                <draggable v-model="tasks"  :move="handleMove" group='task' @end="handleDragEnd">
                <transition-group>
                <Task v-bind:key="task.type"
                 v-for="task in filterTasks(tasks, category.id)"   
                 v-bind:task = "task">
                    {{task.name}}
                 </Task>
                </transition-group>
                </draggable>
            </div>
            <div class="newTask">
                <select v-model="taskType">
                 <option v-for="taskType in taskTypes" v-bind:value="taskType.code" v-bind:key="taskType.code">{{taskType.name}}</option>
                </select>
                <input class="input-add-task" v-model="newTaskName" type="text"/>
                <button class="button-add-column" v-on:click="addTask(category.name)">Add task</button>
             </div>
</div>
</template>

<script>
import Task from './Task.vue'
import { VueDraggableNext } from 'vue-draggable-next'
export default {
    name:"TaskCategory",
    props: ["category","taskTypes"],
    inject: ["tasks", "validator"],
    data: function() {
        return {
            newTaskName: '',
            dragging: false,
        }
    },
     methods: {
        filterTasks: function(tasks,neededType) {
            return tasks.filter(function(task){
                return task.type == neededType;
            })
        },
        handleDragEnd() {
            console.log( 'end');
          },
        handleMove(e) {
             console.log( e.draggedContext)
             const { index, futureIndex } = e.draggedContext;
             console.log(index, futureIndex)
        },
        addTask : function(type) {
            let inputName = this.newTaskName;
            if(this.validator(inputName)) {
            this.tasks.push({
                    name:inputName, 
                    type:type, taskType: this.taskType, deadline: "",
                    description: "",
             })
            this.newTaskName = '';
            this.taskCounter++;
            }
            else alert('empty task')
        }
    },
    components: {Task, draggable: VueDraggableNext}
}
</script>

<style scoped>
 .cat-header{
     margin:4px;
     font-weight: 600;
     text-transform: capitalize;
     background-color: #e6e6e6;
     padding: 4px;
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
.newTask{
    padding:4px;
    background-color: #e6e6e6;
}

</style>