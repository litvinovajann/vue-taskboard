<template>
    <div class="popup" id="popup">
        <label for="taskName"> Task Name</label>
        <input type="text" name= "taskName"  v:value="task.name" >
        <br>
        <br>
        {{task.description}}
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
   methods: {
       close() {
           this.$emit('close');
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