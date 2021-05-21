<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.name {
  width: 100%;
}
.view {
  width: 100%;
  height: 8%;
}
.control {
  width: 100%;
}
.control button {
  width: 50px;
}
.container {
  height: 100vh;
  padding: 10px;
  display: flex;
  width: 100%;
  border: 3px solid black;
  align-items: flex-end;
  flex-wrap: wrap;
  background-color: antiquewhite;
  text-align: center;
}
.container.child {
  height: 65%;
  width: 50%;
  background-color: wheat;
}
.container.child.grandchild {
  height: 55%;
  width: 50%;
  background-color: lightsalmon;
}
</style>
