<template>
    <form 
    class="editItem">
        <input 
        v-model="itemExemple.title"
        v-bind:class="[itemExemple.abcd]"
        placeholder="Title:" type="text">
        <textarea 
        v-model="itemExemple.steps"
        v-bind:class="[itemExemple.abcd]"
        placeholder="Description:"></textarea>
        <ul 
        class="abcd">
            <li 
            v-for="(myClass, index) in color"
            :key="index"
            v-bind:value="myClass"
            v-on:click="abcdColor(myClass)"
            ></li>
            <li v-on:click="info()">&#128712;</li>
        </ul>
    </form>
</template>

<script>
export default {
    props:["itemExemple"],
    data(){
        return{
            abcd: this.abcd,
            color: ['red', 'green', 'yellow', 'blue'],
        }
    },
    methods:{
        abcdColor(myClass){
            this.abcd = myClass
            this.$emit('edit-item', this.abcd);
        },
        info(){
            alert(
                "RED - Tasks that are perceived as being urgent and important;\n" +
                "GREEN - Tasks that are important but not urgent;\n" +
                "YELLOW - Tasks that are unimportant but urgent;\n" +
                "BLUE - Tasks that are unimportant and not urgent;\n" 
            )
        }
    }
}
</script>

<style scoped>
    .editItem{
        border-radius: 0 0 4em 4em;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        background-color: white;
        margin-top: 1em;  
        padding: 1em 0 2em 0;  
        max-width: 100vw;      
    }

    input[type=text]{
        min-width: calc(100% - 2.9em);
        max-width: calc(100% - 2.9em);
        font-size: 2em;
        padding: .5em;
        border-radius: .5em;
        border: none;
        margin-bottom: .2em;
        box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
    }

    textarea{
        min-width: calc(100% - 3.4em);
        max-height: 4em;
        min-height: 1em;
        resize: vertical;
        font-size: 2em;
        padding: .5em;
        border: none;
        border-radius: .5em;
        box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
    }

    .abcd{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        width: calc(100% - 5em);
        margin: .3em;
        padding: .5em;
        border-radius: .5em;
        background-color: white;
        box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
    }

    li{
        width: 1em;
        height: 1em;
        cursor: pointer;
        border: .1em dotted black;
        user-select: none;
    }

    li:nth-child(1){background-color: LightSalmon;color: LightSalmon;}
    li:nth-child(2){background-color: LightGreen;color: LightGreen;}
    li:nth-child(3){background-color: Khaki;color: Khaki;}
    li:nth-child(4){background-color: LightBlue;color: LightBlue;}
    li:nth-child(5){
        font-size: 1em;
        cursor: help;
        border: none;
        position: relative;
        top: -.3em;
        left: .2em;
        font-size: 1.5em;
        line-height: 1em;
    }
    .red{background-color: LightSalmon;}
    .green{background-color: LightGreen;}
    .yellow{background-color: Khaki;}
    .blue{background-color: LightBlue;}
</style>