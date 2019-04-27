/* eslint-disable */
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h3>Todo App version 0.01</h3>
    <input id="_input" type="text" v-model="data" v-on:keyup.enter="addData">
    <button @click="addData('agaya param')" v-show="!updateValueIndex">Add</button>
    <button v-show="updateValueIndex" @click="updateData()">update</button>
    <button v-show="updateValueIndex" @click="updateCancel()">cancel</button>

    <ul v-for="(val, key) in arr">
      <li>{{ val }}</li>
      <button @click="deleteData(key)">Delete</button>
      <button @click="editData(key)">Edit</button>
    </ul>
  </div>
</template>


<script>
export default {
  data() {
    return {
      data: "",
      updateValueIndex: "",
      arr: ["Testig 1", "TTesting 2"]
    };
  },
  methods: {
    addData: function(e) {
      if (!this.updateValueIndex) {
        var a = document.getElementById("_input");
        this.arr.push(a.value || "Empty");
        this.data = "";
      }
    },
    deleteData: function(e) {
      if (!this.updateValueIndex) {
        this.arr.splice(e, 1);
      } else {
        alert("Please cancel Update... Then Delete :)");
      }
    },
    editData: function(e) {
      console.log(e, this.arr);
      // this.arr[e]='updated'
      this.updateValueIndex = e + 1;
      this.data = this.arr[e];
    },
    updateData: function() {
      var dataIndex = this.updateValueIndex - 1;
      var updateValue = this.data;
      this.arr[dataIndex] = updateValue;
      this.updateValueIndex = "";
      this.data = "";
    },
    updateCancel: function() {
      this.updateValueIndex = "";
      this.data = "";
    }
  }
};
</script>



<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
