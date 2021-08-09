<template>
    <div class="popup">
        popup
        <div>
            <!-- <Task>

            </Task> -->
        </div>
    </div>
</template>
<script>
// import Task from "./Task.vue"
export default {
   name:"TaskDetail",
   props: ["task"],
//    components: {Task}
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
</style>