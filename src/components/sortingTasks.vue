<template>
<div class="sortingTasks">
  <ul>
    <li><h5>Sort by:</h5></li>
    <li 
    v-on:click="sort">
      <button value="dateAdd">Added:
        <span class="arrows">
          <div v-bind:class="[(this.sorted=='asc' && this.valueSort=='dateAdd')? 'activeArrow':'']" class="arrow">&#129089;</div>
          <div v-bind:class="[(this.sorted=='desc' && this.valueSort=='dateAdd')? 'activeArrow':'']" class="arrow">&#129091;</div>
        </span>
      </button>
    </li>    
    <li 
    v-on:click="sort">
      <button value="title">Title:
        <span class="arrows">
          <div v-bind:class="[(this.sorted=='asc' && this.valueSort=='title')? 'activeArrow':'']" class="arrow">&#129089;</div>
          <div v-bind:class="[(this.sorted=='desc' && this.valueSort=='title')? 'activeArrow':'']" class="arrow">&#129091;</div>
        </span>
      </button>
    </li>
  </ul>
</div>
</template>

<script>
export default {
    props:["filteredTasks", "sorted", "valueSort"],
    methods:{
      sort(event){
        this.$emit('sort', event.target.value)
      }     
    },
}
</script>

<style scoped>
  .sortingTasks{
    background-color: Azure;
    width: 100vw;
    position: sticky;
    top: 6em;
  }

  h2{padding: .3em;}

  ul {
    overflow: hidden;
    background-color: Azure;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    padding: .5em 2em;
  }

  button {
    border: none;
    font: inherit;
    color: inherit;
    background-color: transparent;
    cursor: pointer;
    padding: .4em .2em;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    border-radius: 1em;
    margin-left: .1em;
    text-decoration: underline;
  }
  li:hover button {
    transition: .35s;
    background-color:DarkGrey;
    color:white;
  }

  .arrows{
    position: relative;
    top: 0;
    left: 0;
    height: .5em;
    padding-right: 1em;
  }

  .arrow:nth-child(1){
    position: absolute;
    top: -.7em;
  }
  .arrow:nth-child(2){
    position: absolute;
    top: -.2em;
  }
  .activeArrow{
    color: Turquoise;
  }
</style>