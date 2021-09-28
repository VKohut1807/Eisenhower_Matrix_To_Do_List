<template>
    <ul class="th">
        <li class="mainEl">
            <input type="checkbox" disabled>
            <h3>Nr:</h3>
            <h3>Title:</h3>
            <h3>Description:</h3>
            <h3>Button group</h3>
        </li>
    </ul>
</template>

<script>
export default {

}
</script>

<style scoped>
    .th{
        position: relative;
        display: flex;
        justify-content: space-between;
        position: sticky;
        top: 0;
        width: 100vw;
        height: 3.1em;
        background-color: Gainsboro;
        box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
        z-index: 3;
    }

    .mainEl{
        display: flex;
        flex-direction: row;
        align-items: center;
        width: 100%;
    }

    input{
        zoom: 2.5;
    }

    h3{
        margin: 0 1em;
    }

    h3:nth-child(2){
        margin: 0 .35em;
    }

    h3:nth-child(4){
        margin-left: 1em;
    }
    
    h3:nth-child(5){
        margin: 0 .25em 0 auto;
    }
</style>