<template>
  <div class="list">
    <div class="item">
      <div class="icon-check">
        <img src="@/assets/images/check.png" alt="完成" />
      </div>
      <div class="task" style="text-decoration:line-through">厦控股的吉安分公司的</div>
      <div class="icon-delete">
        <img src="@/assets/images/delete.png" alt="删除" />
      </div>
    </div>
    <div class="item">
      <div class="icon-check"></div>
      <div class="task">上岛咖啡广东省科技分</div>
      <div class="icon-delete"></div>
    </div>
    <div class="item">
      <div class="icon-check"></div>
      <div class="task">价格约为</div>
      <div class="icon-delete"></div>
    </div>
  </div>
</template>

<script lang="ts">
import {
  defineComponent,
  ref,
  reactive,
  onMounted,
  onUpdated,
  onUnmounted
} from "vue";

export default defineComponent({
  name: "todo list",
  props: {
    msg: String
  },
  setup(props) {
    // interface Data {
    //   count: number;
    //   object: object;
    // }
    const count = ref(0);
    const object = reactive({ foo: "bar" });
    const increase = (): void => {
      count.value++;
    };
    const list: Array<object> = [
      {
        name: "foo"
      },
      {
        name: "bar"
      },
      {
        name: "coo"
      }
    ];
    function test(x: number): string {
      console.log(x);
      return props.toString();
    }
    test(1);
    // test('number');
    // 生命周期
    onMounted(() => {
      console.log("mounted vue3 typescript");
    });
    onUpdated(() => {
      console.log("updated vue3 typescript");
    });
    onUnmounted(() => {
      console.log("onUnmounted vue3 typescript");
    });
    // 暴露给模板
    return {
      count,
      increase,
      object,
      list
    };
    // return () => h('div', [count.value, object.foo])
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.list {
  .item {
    display: flex;
    padding: 6px 10px;
    height: 40px;
    border-bottom: 1px solid #f1f3f1;
    .icon-check {
      width: 34px;
      height: 34px;
      border: 1px solid #f5f5f6;
      border-radius: 50%;
      cursor: pointer;
      img {
        width: 100%;
      }
    }
    .task {
      flex: 1;
      font-size: 20px;
      text-align: left;
      padding-left: 12px;
      line-height: 36px;
    }
    .icon-delete {
      width: 22px;
      cursor: pointer;
      img {
        margin-top: 9px;
        width: 100%;
      }
    }
  }
}
</style>
