<template>
    <div class="popup" id="popup" v-bind:task="task">
        popup
        {{task}}
        <div class="closeButton" v-on:click="hideTask">
        х
        </div>
    </div>
</template>
<script>
export default {
   name:"TaskDetail",
   props: ["task"],
   methods: {
        hideTask: () => {
            const popup = document.getElementById("popup");
            popup.style.display="none"
        } 
   },
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