<template>
  <div class="container child">
    <div class="name">{{ name }}</div>
    <div class="view">{{ message }}</div>
    <div class="control">
      <button @click="parent(name)">親</button>
      <button @click="view(name)">自分</button>
      <button @click="childView(name)">子供</button>
      <button @click="brotherView(name)">兄弟</button>
    </div>
    <Grandchild1-1
      ref="child"
      @grandparent="parent($event)"
      @grandbrother="grandbrother($event)"
    />
    <Grandchild1-2 />
  </div>
</template>
<script>
export default {
  props: [
    named
  ],
  data() {
    return {
      name: "家光",
      message: ""
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
      this.$refs.child.view(name);
    },
    brotherView(name) {
      this.$emit("brother", name);
    },
    parent(name) {
      this.$emit("parent", name);
      // console.log("go");
    },
    grandbrother(name) {
      this.$emit("grandbrother", name);
      // console.log("go");
    }
  }
};
</script>
