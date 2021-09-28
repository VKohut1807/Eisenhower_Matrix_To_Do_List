<template>
  <div class="notes">
    <titleTasks
    />
    <filterTasksABCD
    v-on:change="onFilterChanged"
    />
    <loader v-if="loading"/>
    <listView
      v-bind:filteredTasks="filteredTasks"
      v-on:removeItem="onRemoveItem"
      v-else-if="filteredTasks.length"
    />
    <zeroTasks
      v-bind:filter="filter"
      v-else
    />
    <addItem
      v-on:add-item="addElem"
    />
  </div>
</template>

<script>
import titleTasks from "../components/titleTasks.vue"
import listView from "../components/listView.vue"
import addItem from "../components/addItem.vue"
import zeroTasks from "../components/zeroTasks.vue"
import loader from "../components/loader.vue"
import filterTasksABCD from "../components/filterTasksABCD.vue"
export default {
  name: 'tasksABCD',
  components: {
    titleTasks, listView, addItem, zeroTasks, loader, filterTasksABCD
  },
  data(){
    return {
      sampleAssignments: [],
      loading: true,
      filter: 'all',
      colors: ["red", "green", "yellow", "blue"],
      color: '',
    }
  },
  methods:{
    onFilterChanged(value) {
      this.filter = value
    },
    addElem(event){
      this.sampleAssignments.push(event)
    },
    onRemoveItem(id){
      this.sampleAssignments = this.sampleAssignments.filter(t => t.id !== id)
    },
  },
  mounted(){
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=7')
    .then(response => response.json())
    .then(json => {
      setTimeout(() => {
        for(let key in json){
          this.sampleAssignments.push({
            id: json[key].id, 
            title: json[key].title, 
            steps: "Doing " + json[key].completed + json[key].title + json[key].completed,
            completed: json[key].completed,
            abcd: this.color = this.colors[Math.round(Math.random()*(this.colors.length-0.5))],
            dateAdd: new Date().toLocaleString()
          })
        }
        this.loading = false
      }, 500)
    })
  },
  computed:{
    filteredTasks(){
      if(this.filter === 'all'){
        return this.sampleAssignments
      } else if (this.filter === 'completed'){
        return this.sampleAssignments.filter(t => t.completed)
      } else if(this.filter === 'notCompleted'){
        return this.sampleAssignments.filter(t => !t.completed)
      }
      
      else if (this.filter === 'red'){
        return this.sampleAssignments.filter(t => t.abcd === 'red')
      } else if (this.filter === 'redC'){
        return this.sampleAssignments.filter(t => t.abcd === 'red' && t.completed)
      } else if (this.filter === 'redN'){
        return this.sampleAssignments.filter(t => t.abcd === 'red' && !t.completed)
      }
      
      else if (this.filter === 'green'){
        return this.sampleAssignments.filter(t => t.abcd === 'green')
      } else if (this.filter === 'greenC'){
        return this.sampleAssignments.filter(t => t.abcd === 'green' && t.completed)
      } else if (this.filter === 'greenN'){
        return this.sampleAssignments.filter(t => t.abcd === 'green' && !t.completed)
      } 
      
      else if (this.filter === 'yellow'){
        return this.sampleAssignments.filter(t => t.abcd === 'yellow')
      } else if (this.filter === 'yellowC'){
        return this.sampleAssignments.filter(t => t.abcd === 'yellow' && t.completed)
      } else if (this.filter === 'yellowN'){
        return this.sampleAssignments.filter(t => t.abcd === 'yellow' && !t.completed)
      } 
      
      else if (this.filter === 'blue'){
        return this.sampleAssignments.filter(t => t.abcd === 'blue')
      } else if (this.filter === 'blueC'){
        return this.sampleAssignments.filter(t => t.abcd === 'blue' && t.completed)
      } else if (this.filter === 'blueN'){
        return this.sampleAssignments.filter(t => t.abcd === 'blue' && !t.completed)
      }

      else {
        return []
      }
    },
  }
}
</script>

<style scoped>

</style>