<template>
    <div>
    <div   @click="showPopup" class="task">
        <div>
           <h2>{{task.name}} </h2>
           <p>Author: {{task.author}}</p>
           <p>Type: {{task.taskType}}</p>
        </div>
    </div>
    <div>
        <TaskDetail v-show="modalShown"  v-bind:task="task" v-bind:key="task.type" @close="closePopup">
        </TaskDetail>
    </div>
    </div>
</template>

<script>
import TaskDetail from "./TaskDetail.vue"
export default {
    name:"Task",
    props: ["task"],
    data: function() {
        return {
            modalShown: false,
        }
    },
    methods: {     
        showPopup: function() {
            this.modalShown = true;
        },
        closePopup: function() {
            this.modalShown = false;
        }
    },
    components: {
        TaskDetail,
    }
}
</script>

<style scoped>
  .task {
      border: 2px solid #e6e6e6;
    border-radius: 4px;
    margin: 4px;
    font-size: 12px;
  }
  .task h2{
      font-size: 14px;
      padding:0;
      margin: 2px;
  }
  .task p {
      padding: 0;
      margin:2px;
  }
  
</style>