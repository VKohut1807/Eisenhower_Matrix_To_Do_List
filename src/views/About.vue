<template>
  <div class="about">
    <h2>The Eisenhower Method</h2>
    <p>Eisenhower's specific professional activities constantly forced him to make tough decisions and focus on different tasks every day. To optimize the process, he created his own method, which became widely known as the Eisenhower matrix. Today, it can be used not only by generals, but also by ordinary people up to housewives - it helps to prioritize current tasks and put things in order.</p>
    <h4>How to use the Eisenhower matrix</h4>
    <p>
      <ul>
          <li class="red">RED color - Tasks that are perceived as being urgent and important;</li>
          <li class="green">GREEN color - Tasks that are important but not urgent;</li>
          <li class="yellow">YELLOW color - Tasks that are unimportant but urgent;</li>
          <li class="blue">BLUE color - Tasks that are unimportant and not urgent;</li>
      </ul>
    </p>
    <p class="conclusion">The ultimate goal of the Eisenhower Method is to help filter out minor matters from important decisions and focus on what really matters.</p>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
  .about{
    display: flex;
    flex-direction: column;
    padding: 1em;
  }

  h2, h4{text-align: center;}
  p{padding: 1em;}

  li{
    padding: .5em;
    margin: 0 .5em;
  }

  .conclusion{font-weight: bold;}
  .red{background-color: LightSalmon;}
  .green{background-color: LightGreen;}
  .yellow{background-color: Khaki;}
  .blue{background-color: LightBlue;}
</style>