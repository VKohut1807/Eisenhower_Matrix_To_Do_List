<template>       
    <li
    v-bind:class="
    [item.abcd == 'red'? 'red':'',
    item.abcd == 'green'? 'green':'',
    item.abcd == 'yellow'? 'yellow':'',
    item.abcd == 'blue'? 'blue':''
    ]"
    class="listItem">
        <div class="mainEl">
            <input v-model="item.completed" type="checkbox">    
            <h2
            v-bind:class="{performed: item.completed}"
            >{{index+1}}</h2>
            <h4
            v-bind:class="{performed: item.completed}"
            >{{item.title}}</h4>
            <p>{{item.completed? "GOOD JOB!":item.steps}}</p>
            <div class="buttonGroup">
                <button
                v-on:click="(visibleEdit = !visibleEdit)"
                v-if="!item.completed"
                class="edit">&#9998;
                </button>
                <button
                v-on:click="$emit('remove', item.id)"
                class="del">&times;
                </button>        
            </div>  
        </div>
        <transition 
            name="custom-classes-transition"
            enter-active-class="animated tada"
            leave-active-class="animated bounceOutRight">
            <editItem
                v-if="item.completed == false && visibleEdit"
                v-bind:itemExemple="item"
                v-on:edit-item="editElem"
            />
        </transition>
    </li>
</template>
<script>
import editItem from "./editItem.vue"
export default {
    components: {
        editItem
    },
    props: {
        item: {
            type: Object,
            required: true
        },
        index: Number,
    },
    data(){
        return{
            visibleEdit: false,
        }
    },
    methods:{
        editElem(event){
            this.item.dateAdd = new Date().toLocaleString()
            this.item.abcd = event
        }
    }
}
</script>

<style scoped>
    .listItem{
        display: flex;
        flex-direction: column;
        border: .1em solid black;
        border-top-style: none;
        border-left-style: none;
        border-right-style: none;
        padding: 1em 0;
        width: 100vw;
    }

    .mainEl{
        display: flex;
        flex-direction: row;
        align-items: center;
        width: 100vw;
    }

    input{
        cursor: pointer;
        zoom: 2.5;
    }

    h2{margin: 0 .4em;}
    h4{width: 33%;}

    p{
        width: 30%;
        margin: 0 .3em;
        text-overflow: ellipsis;
    }

    .buttonGroup{
        display: flex;
        justify-content: flex-end;
        flex-direction: row;
        margin-left: auto;
    }

    button{
        width: 3em;
        height: 3em;
        border-radius: 50%;
        cursor: pointer;
    }

    button:hover{background-color: white;}

    .edit{background-color: yellow;}

    .del{
        background-color: brown;
        margin-left: .1em;
    }

    .red{background-color: LightSalmon;}
    .green{background-color: LightGreen;}
    .yellow{background-color: Khaki;}
    .blue{background-color: LightBlue;}

    .performed{text-decoration: line-through;}
</style>