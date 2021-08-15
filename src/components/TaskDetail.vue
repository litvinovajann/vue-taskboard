<template>
    <div class="popup" id="popup">
       <h1>{{task.name}}</h1>
        <div>{{task.author}}</div>
        <div>{{task.difficulty}}</div>
        <div>{{task.description}} </div>
        <div>{{task.deadline}}</div> 
        <button @click="showTaskEditing">Edit Task</button>
        <div v-show="editTaskShown" class="editTask">
            <input type="text" v-model="TaskData.name">
            <input type="text" v-model="TaskData.author">
            <textarea type="text" v-model="TaskData.description"/>
            <input type="text" v-model="TaskData.deadline">
            <button @click ="editTask">Update</button>
        </div>
        <div class="closeButton" @click="close">
        х
        </div>
        
    </div>
</template>
<script>
export default {
   name:"TaskDetail",
   props: ["task"],
   inject: ["tasks"],
   computed: {
       TaskData: function() {
           return this.tasks.find(el => el.id === this.task.id);
       }
   },
   data: function() {
       return {
           editTaskShown: false,
       }
   },
   methods: {
       close() {
           this.$emit('close');
           return true;
       },
       showTaskEditing() {
           this.editTaskShown = true;
       },
       editTask() {
            this.editTaskShown = false;
            return true;
       }
   }
}
</script>
<style>
    .popup {
        background-color: #dcdcdc75;
        width:100%;
        height: 100vh;
        position: absolute;
        top: 0;
    }
    .closeButton{
        font-weight: 700;
        cursor: pointer;
        width: 30px;
        position: absolute;
        height: 30px;
        font-size: 50px;
        right: 0;
        margin: 10px;
    }
</style>