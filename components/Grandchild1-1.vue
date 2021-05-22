<template>
  <div class="container child grandchild">
    <div class="name">{{ name }}</div>
    <div class="view">{{ message }}</div>
    <input type="text" v-model="granpare" />
    <div class="control">
      <button @click="grandparent()">親の親</button>
      <button @click="view(name)">自分</button>
      <button @click="grandbrother()">いとこ</button>
    </div>
  </div>
</template>
<script>
export default {
  props: ["named"],
  data() {
    return {
      name: this.named,
      message: "",
      granpare: "家康"
    };
  },
  watch: {
    named: function() {
      this.name = this.named;
    },
    granpare: function(){
      this.$emit("granRename", this.granpare);
    }
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
    },
  }
};
</script>
