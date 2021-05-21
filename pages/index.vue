<template>
  <div class="container">
    <div class="name">{{ name }}</div>
    <div class="view">{{ message }}</div>
    <div class="control">
      <button @click="view(name)">自分</button>
      <button @click="childView(name)">子供</button>
      <button @click="grandchildView(name)">孫</button>
    </div>
    <Child1
      named="aaa"
      ref="child1"
      @parent="view($event)"
      @brother="childView2($event)"
      @grandbrother="grandchildView2($event)"
    />
    <Child2
      :named='name2'
      ref="child2"
      @parent="view($event)"
      @brother="childView1($event)"
      @grandbrother="grandchildView1($event)"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "家康",
      message: "",
      name1:"家光",
      name2:"家闇"
    };
  },
  methods: {
    view(name) {
      this.message = name + "に呼ばれた！";
      setTimeout(this.clear, 1000);
    },
    clear: function() {
      this.message = "";
    },
    childView(name) {
      this.childView1(name);
      this.childView2(name);
    },
    childView1(name) {
      this.$refs.child1.view(name);
    },
    childView2(name) {
      this.$refs.child2.view(name);
    },
    grandchildView(name) {
      this.grandchildView1(name);
      this.grandchildView2(name);
    },
    grandchildView1(name) {
      this.$refs.child1.childView(name);
    },
    grandchildView2(name) {
      this.$refs.child2.childView(name);
    },
    test() {
      console.log("arrive");
    }
  }
};
</script>
