<template>
  <div class="todo">
    <div class="todo-title">
      <span><slot name="title">{{ data.title }}  [{{ data.doneItems }}/{{data.items.length}}]</slot></span>
    </div>
    <div class="todo-items">
      <ul>
        <li v-for="(item, index) in data.items" :key="index">
          <div class="todo-item" @click="toggleItem(index)">
            <div class="todo-item-title">
              <span :class="{'todo-item-checked' : item.isDone }">{{ item.title }}</span>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "ToDo.vue",
  props: {
    data: {
      type: Array,
      required: true
    }
  },
  methods: {
    toggleItem(index: number) {
      this.data.items[index].isDone = !this.data.items[index].isDone;
      this.data.doneItems = this.data.items.filter((item: any) => item.isDone).length;
      this.$emit("update", this.data);
    }
  },
})
</script>

<style lang="scss">
.todo {
  padding: 43px 35px;

  &-items {
    margin-top: 45px;
  }

  &-item {
    &-checked {
      text-decoration: line-through;
    }
  }

  &-title {
    font-family: 'Average Sans',sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 30px;
    line-height: 39px;
    color: #1E1E1E;
  }
}
</style>