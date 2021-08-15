<template>
    <div @click="showPopup" class="task">
        <div>
           <h2>Name: {{task.name}} </h2>
           <p>Author: {{task.author}}</p>
        </div>
    </div>
    <div>
        <TaskDetail v-show="modalShown"  v-bind:task="task" v-bind:key="task.type" @close="closePopup">
        </TaskDetail>
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
        TaskDetail
    }
}
</script>

<style scoped>
  
  
</style>