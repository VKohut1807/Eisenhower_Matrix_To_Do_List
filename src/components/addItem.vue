<template>
  <div>
    <transition name="list">
      <form
        v-show="shawAddEl"
        v-on:submit.prevent="onSubmit"
        class="addElem"
        autocomplete="off"
      >
        <input
          v-model="title"
          v-bind:class="[!this.title.trim() ? 'trim' : 'noTrim', abcd]"
          type="text"
          placeholder="Title:"
        />
        <textarea
          v-model="steps"
          placeholder="Description:"
          v-bind:class="[!this.steps.trim() ? 'trim' : 'noTrim', abcd]"
        ></textarea>
        <ul class="abcd noTrim">
          <li
            v-for="(myClass, index) in color"
            :key="index"
            v-bind:value="myClass"
            v-on:click="abcdColor(myClass)"
          ></li>
          <li v-on:click="info()">&#128712;</li>
        </ul>
        <button
          type="submit"
          class="Send"
          v-bind:disabled="isDisabled"
          v-bind:class="[
            !this.title.trim() || !this.steps.trim() ? 'falseSend' : 'trueSend',
          ]"
        >
          <div>
            {{
              !this.title.trim() || !this.steps.trim() ? "&#8722;" : "&#10003;"
            }}
          </div>
        </button>
      </form>
    </transition>
    <button
      type="submit"
      v-on:click="shawAddEl = !shawAddEl"
      class="shawAddComponent"
    >
      <div>{{ !shawAddEl ? "&#43;" : "&#129192;" }}</div>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      steps: "",
      abcd: "blue",
      shawAddEl: false,
      color: ["red", "green", "yellow", "blue"],
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim() && this.steps.trim()) {
        const addItem = {
          id: Date.now(),
          title: this.title,
          steps: this.steps,
          abcd: this.abcd,
          completed: false,
          dateAdd: new Date().toLocaleString(),
        };
        this.$emit("add-item", addItem);
        this.title = "";
        this.steps = "";
        this.abcd = "blue";
      }
    },
    abcdColor(myClass) {
      this.abcd = myClass;
    },
    info() {
      alert(
        "RED - Tasks that are perceived as being urgent and important;\n" +
          "GREEN - Tasks that are important but not urgent;\n" +
          "YELLOW - Tasks that are unimportant but urgent;\n" +
          "BLUE - Tasks that are unimportant and not urgent;\n"
      );
    },
  },
  computed: {
    isDisabled() {
      return !this.title || !this.steps;
    },
  },
};
</script>

<style scoped>
.addElem {
  position: fixed;
  bottom: 4.9em;
  left: 0;
  right: 0;
  display: flex;
  flex-direction: column;
  z-index: 3;
}

input[type="text"] {
  min-width: calc(100% - 3.1em);
  max-width: calc(100% - 3.1em);
  font-size: 2em;
  margin: 0.1em;
  padding: 0.5em;
  border-radius: 0.5em;
  box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
}

textarea {
  min-width: calc(100% - 3.5em);
  max-width: calc(100% - 3.5em);
  max-height: 4em;
  min-height: 1em;
  resize: vertical;
  font-size: 2em;
  margin: 0.1em;
  padding: 0.5em;
  border-radius: 0.5em;
  box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
}

.abcd {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: calc(100% - 8em);
  margin: 0.1em 0.3em;
  padding: 0.5em;
  border-radius: 0.5em;
  background-color: white;
  box-shadow: 0px 2px 10px 5px rgba(0, 0, 0, 0.2);
}

li {
  width: 1em;
  height: 1em;
  cursor: pointer;
  border: 0.1em dotted black;
  user-select: none;
}

li:nth-child(1) {
  background-color: LightSalmon;
  color: LightSalmon;
}
li:nth-child(2) {
  background-color: LightGreen;
  color: LightGreen;
}
li:nth-child(3) {
  background-color: Khaki;
  color: Khaki;
}
li:nth-child(4) {
  background-color: LightBlue;
  color: LightBlue;
}
li:nth-child(5) {
  font-size: 1em;
  cursor: help;
  border: none;
  position: relative;
  top: -0.3em;
  left: 0.2em;
  font-size: 1.5em;
  line-height: 1em;
}

.Send {
  position: fixed;
  right: 1.3em;
  bottom: 9.3em;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  padding: 0.75em;
  font-weight: bold;
  width: 3em;
  height: 3em;
  cursor: pointer;
  font-size: 1.3em;
}

.shawAddComponent {
  position: fixed;
  right: 0.2em;
  bottom: 1em;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  border: 0.1em solid Turquoise;
  font-size: 3em;
  padding: 0.75em;
  background-color: Aquamarine;
  color: white;
  font-weight: bold;
  width: 1em;
  height: 1em;
  cursor: pointer;
  z-index: 3;
  transition: 1s;
}

.shawAddComponent:hover {
  background-color: white;
  transition: 1s;
  color: black;
}

.noTrim {
  border: 0.1em solid green;
}
.trim {
  border: 0.1em solid red;
}

.trueSend {
  color: green;
  background-color: Lime;
}
.falseSend {
  color: red;
  background-color: Salmon;
}

.red {
  background-color: LightSalmon;
}
.green {
  background-color: LightGreen;
}
.yellow {
  background-color: Khaki;
}
.blue {
  background-color: LightBlue;
}

.list-enter-active {
  animation: add-item 1s;
}
.list-leave-active {
  position: absolute;
  animation: add-item 1s reverse;
}
.list-move {
  transition: transform 1s;
}
@keyframes add-item {
  0% {
    opacity: 0;
    transform: translateX(150px);
  }
  50% {
    opacity: 0.5;
    transform: translateX(-10px) skewX(20deg);
  }
  100% {
    opacity: 1;
    transform: translateX(0px);
  }
}
</style>