<template>
<div class="footer">
  <nav class="menu">
    <ul>
      <li><router-link to="/" class="linkTo">Home</router-link></li>
      <li><router-link to="/tasks" class="linkTo">Tasks</router-link></li>
      <li><router-link to="/about" class="linkTo">About</router-link></li>
    </ul>
  </nav>  
</div>

</template>

<script>
export default {
  
}
</script>

<style scoped>
  .footer{
    position: fixed;
    bottom: 0;
    left: 0;
    background-color: Gainsboro;
    min-height: .5em;
    width: 100vw;
    height: 2.5em;
  }

  .menu {
    position: fixed;
    bottom: -1em;
    left: calc(50% - 1.5em);
    background-color: white;
    width: 3em;
    height: 3em;
    border-radius: 50%;
    cursor: pointer;
    transition: 1s;
    border: 1em solid LightGray;
  }

  .menu:after {
    content: "";
    position: absolute;
    top: 1em;
    left: 1em;
    width: 1em;
    height: 0.15em;
    border-top: 0.6em double black;
    border-bottom: 0.2em solid black;
    transition: 1s;
  }

  .menu:hover{
    background-color: DarkGray;
    transition: 1s;
  }
  .menu:hover:after{
    transition: 1s;
    border-color:white;
  }

  .menu li {
    text-align: center;
    border-radius: 100%;
    opacity: 0;
    z-index: -1;
  }

  .menu:hover li {opacity: 1;}
  .menu ul {transition: 1s all;}
  .menu:hover ul {transform: rotate(270deg) translateY(-1em);}
  .menu li:hover {z-index: 3;}

  .menu li:nth-of-type(1) {
    transform: rotate(120deg);
    position: absolute;
    left: 0em;
    top: -3.5em;
    transition: 1.5s;
  }

  .menu li:nth-of-type(2) {
    transform: rotate(90deg);
    position: absolute;
    left: 1em;
    top: 0em;
    transition: 1s;
  }

  .menu li:nth-of-type(3) {
    transform: rotate(60deg);
    position: absolute;
    left: 0em;
    top: 3.5em;
    transition: .5s;
  }

  .linkTo{
    color: black;
    font-weight: bold;
    line-height: 2em;
    border-radius: 100%;
    background-color: LightGray;
    padding: 1em;
    transition: 1s;
  }

  .linkTo:hover{background-color: DarkGray;transition: 1s}
  .menu li:nth-of-type(2) .linkTo{padding: 1.5em;}
</style>