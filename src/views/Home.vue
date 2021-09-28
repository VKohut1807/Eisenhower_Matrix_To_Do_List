<template>
  <div class="home">
    <h2>Eisenhower Matrix: A Simple Tool for Distributing Problems</h2>
    <p>Most people spend time deciding their priorities.</p>
    <router-link to="/about" class="linkTo">To learn more...</router-link>
    <router-link to="/tasks" class="linkTo"
      ><h1>Eisenhower Matrix (To Do List)</h1>
    </router-link>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.home {
  padding: 1em;
}
h2 {
  text-align: center;
}
p {
  margin: 1em 0;
}
.linkTo {
  display: flex;
  flex-direction: column;
  margin: 25px auto;
}

h1 {
  margin: 0 auto;
  color: Turquoise;
}
</style>