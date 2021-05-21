<template>
  <div class="container child grandchild">
    <div class="name">{{ name }}</div>
    <div class="view">{{ message }}</div>
    <div class="control">
      <button @click="grandparent()">親の親</button>
      <button @click="view(name)">自分</button>
      <button @click="grandbrother()">いとこ</button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "闇太郎",
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
    grandparent() {
      this.$emit("grandparent", this.name);
      // console.log("go");
    },
    grandbrother() {
      this.$emit("grandbrother", this.name);
      // console.log("go");
    }
  }
};
</script>
