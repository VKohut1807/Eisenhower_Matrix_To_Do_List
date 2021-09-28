<template>
<div class="filterABCD">
  <ul>
    <li><h5>Filters:</h5></li>
    <li 
    v-on:click="filterTasks" class="dropdown">
      <button
      value="all"
      class="dropbtn">All Tasks</button>
      <div class="dropdown-content">
        <button
        value="completed"
        >Completed</button>
        <button 
        value="notCompleted"
        >Not Completed</button>
      </div>
    </li>
    <li
    v-on:click="filterTasks" class="dropdown">
      <button
      value="red"
      class="dropbtn">Red</button>
      <div class="dropdown-content">
        <button
        value="redC"
        >Completed</button>
        <button 
        value="redN"
        >Not Completed</button>
      </div>
    </li>
    <li
    v-on:click="filterTasks" class="dropdown">
      <button
      value="green"
      class="dropbtn">Green</button>
      <div class="dropdown-content">
        <button
        value="greenC"
        >Completed</button>
        <button 
        value="greenN"
        >Not Completed</button>
      </div>
    </li>
    <li
    v-on:click="filterTasks" class="dropdown">
      <button
      value="yellow"
      class="dropbtn">Yellow</button>
      <div class="dropdown-content">
        <button
        value="yellowC"
        >Completed</button>
        <button 
        value="yellowN"
        >Not Completed</button>
      </div>
    </li>
    <li
    v-on:click="filterTasks" class="dropdown">
      <button
      value="blue"
      class="dropbtn">Blue</button>
      <div class="dropdown-content">
        <button
        value="blueC"
        >Completed</button>
        <button 
        value="blueN"
        >Not Completed</button>
      </div>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  methods: {
    filterTasks(event){
      this.$emit('change', event.target.value)
    }
  }
}
</script>

<style scoped>
  .filterABCD{
    position: sticky;
    top: 3.1em;
    width: 100vw;
    background-color: Azure;
    z-index: 3;
  }

  h2{
    padding: .3em;
  }

  ul {
    overflow: hidden;
    background-color:Azure;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    padding: .5em 2em;
  }

  li button, .dropbtn {
    display: inline-block;
    padding: .4em .2em;
    text-decoration: underline;
  }

  .dropbtn {
    margin-left: .1em;
  }

  li:hover button{transition: .35s;}
  li:hover:nth-child(2) button{background-color: Grey;color:white;}
  li:hover:nth-child(3) button{background-color: LightSalmon;color:black;}
  li:hover:nth-child(4) button{background-color: LightGreen;color:black;}
  li:hover:nth-child(5) button{background-color: Khaki;color:black;}
  li:hover:nth-child(6) button{background-color: LightBlue;color:black;}

  li:hover:nth-child(2) button:hover{background-color: DimGray;}
  li:hover:nth-child(3) button:hover{background-color: DarkSalmon;}
  li:hover:nth-child(4) button:hover{background-color: SpringGreen;}
  li:hover:nth-child(5) button:hover{background-color: Moccasin;}
  li:hover:nth-child(6) button:hover{background-color: SkyBlue;}

  .dropdown-content {
    display: none;
    position: absolute;
    box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
    z-index: 1;
    margin-left: .1em;
  }

  button {
    border: none;
    font: inherit;
    color: inherit;
    background-color: transparent;
    cursor: pointer;
    width: 100%;
  }

  .dropdown-content button {
    display: block;
    text-align: left;
  }

  .dropdown:hover .dropdown-content {display: block;}
</style>