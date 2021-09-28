<template>
  <ul class="list-group">
    <sortingTasks
      v-bind:filteredTasks="filteredTasks"
      v-bind:sorted="sorted"
      v-bind:valueSort="valueSort"
      v-on:sort="sortingAscOrDesc"
    />
    <transition-group name="list">
      <listItem
        v-for="(item, index) in filteredTasks"
        :key="item.id"
        v-bind:item="item"
        v-bind:index="index"
        v-on:remove="removeItem"
      />
    </transition-group>
  </ul>
</template>

<script>
import listItem from "./listItem";
import sortingTasks from "./sortingTasks";
export default {
  components: {
    listItem,
    sortingTasks,
  },
  props: ["filteredTasks"],
  data() {
    return {
      sortedTasks: [],
      sorted: "asc",
      valueSort: "dateAdd",
    };
  },
  methods: {
    removeItem(id) {
      this.$emit("removeItem", id);
    },
    sortingAscOrDesc(value) {
      this.sortedTasks = this.filteredTasks;
      if (value == "title") {
        this.valueSort = value;
        if (this.sorted == "desc") {
          this.sortedTasks.sort((a, b) => {
            return a.title < b.title ? -1 : 1;
          });
          this.sorted = "asc";
        } else {
          this.sortedTasks.sort((a, b) => {
            return a.title > b.title ? -1 : 1;
          });
          this.sorted = "desc";
        }
      } else if (value == "dateAdd") {
        this.valueSort = value;
        if (this.sorted == "desc") {
          this.sortedTasks.sort((a, b, x) => {
            return a.dateAdd < b.dateAdd ? -1 : 1;
          });
          this.sorted = "asc";
        } else {
          this.sortedTasks.sort((a, b) => {
            return a.dateAdd > b.dateAdd ? -1 : 1;
          });
          this.sorted = "desc";
        }
      } else {
        this.sortedTasks;
      }
      this.filteredTasks = this.sortedTasks;
      return this.filteredTasks;
    },
  },
};
</script>

<style scoped>
.list-group {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

li:last-child {
  margin-bottom: 4em;
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