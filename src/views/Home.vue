<template>
  <div class="home">
    <div class="box">
      <div class="input-todo">
        <input type="text" placeholder="接下去要做什么?" @keypress="addTask($event)" />
      </div>
      <TodoList :list="list"></TodoList>
      <div class="menus">
        <div class="left">0 items left</div>
        <div class="menu">
          <div class="menu-item active">all</div>
          <div class="menu-item">active</div>
          <div class="menu-item">completed</div>
        </div>
        <div class="clear">clear completed</div>
      </div>
    </div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  </div>
</template>

<script lang="ts">
// @ is an alias to /src
import TodoList from "@/components/TodoList.vue";
import { defineComponent, watchEffect } from "vue";

export default defineComponent({
  name: "Home",
  components: {
    TodoList
  },
  setup() {
    const list: Array<object> = [];
    const addTask = (event: any) => {
      const keyCode = event.keyCode;
      if (keyCode == 13) {
        list.push({
          name: event.target.value,
          complete: false
        });
      }
    };
    watchEffect(() => console.log(list));
    // 暴露给模板
    return {
      addTask,
      list
    };
    // return () => h('div', [count.value, object.foo])
  }
});
</script>

<style lang="less">
.home {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  padding: 30px;
  padding-top: 130px;
  background-color: #f5f5f6;
  .box {
    width: 600px;
    height: auto;
    background-color: #fff;
    margin: 0 auto;
    .input-todo {
      width: 100%;
      height: 50px;
      line-height: 50px;
      border-bottom: 1px solid #f1f3f1;
      input {
        width: 520px;
        height: 36px;
        border: none;
        outline: none;
        font-size: 18px;
      }
      input::-webkit-input-placeholder {
        color: #919392;
      }
      input::-moz-input-placeholder {
        color: #919392;
      }
      input::-ms-input-placeholder {
        color: #919392;
      }
    }
    .menus {
      display: flex;
      height: 34px;
      line-height: 34px;
      padding: 5px 15px;
      .left {
        width: 160px;
        text-align: left;
        cursor: pointer;
      }
      .menu {
        display: flex;
        flex: 1;
        .menu-item {
          border-radius: 5px;
          padding: 0 8px;
          margin: 0 5px;
          cursor: pointer;
        }
        .active {
          border: 1px solid #f58a8a;
        }
      }
      .clear {
        width: 150px;
        text-align: right;
        cursor: pointer;
      }
    }
  }
}
</style>
