<template>
    <div class="popup" id="popup">
          <div class="closeButton" @click="close">
        х
        </div>
       <h1>{{task.name}}</h1>
        <div>author: {{task.author}}</div>
         <div>persormer: {{task.performer}}</div>
        <div>difficulty: {{task.difficulty}}</div>
        <div>description: {{task.description}} </div>
        <div>deadline: {{task.deadline}}</div> 
        <button @click="showTaskEditing">Edit Task</button>
        <div v-show="editTaskShown" class="editTaskWrapper">
                <div  class="editTask">
                    <input type="text" v-model="TaskData.name">
                    <input type="text" v-model="TaskData.author">
                    <input type="text" v-model="TaskData.performer">
                    <textarea type="text" v-model="TaskData.description"/>
                    <input type="text" v-model="TaskData.deadline">
                <div><button @click ="editTask">Update</button> </div>
        </div>
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
        left: 0;
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
    .editTaskWrapper{
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        background-color: #f5dce9a6;
    }
    .editTask{
        display: flex;
        width:50%;
        margin: 4% auto;
    }
    .editTask input, textarea{
        min-height: 100px;
    }
    .editTask textarea{
        min-width: 200px;
    }
    .editTask div {
        width: 100%;
        align-self: center;
    }
</style>