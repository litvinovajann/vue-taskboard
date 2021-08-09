<template>
    <div class="task">
        <div v-on:click="showDetailInfo()">
            {{task.name}}
        </div>
    </div>
</template>

<script>
import TaskDetail from "./TaskDetail.vue"
import {defineComponent, createApp} from "vue";

export default {
    name:"Task",
    props: ["task"],

    methods: {
         showDetailInfo: () => {
            let taskDetailComponent = defineComponent({
                extends: TaskDetail
            });
            const div = document.createElement("div");
            document.getElementById("task-detail").appendChild(div);
            createApp(taskDetailComponent).mount(div);
        }           
    },
}
</script>

<style scoped>

</style>