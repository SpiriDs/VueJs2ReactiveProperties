<template>
  <div id="app1">
    <!-- 1) Show a "result" of 'not there yet' as long as "value" is not equal to 37 - you can change "value" with the buttons. Print 'done' once you did it -->
    <div>
        <p>Current Value: {{ value}}</p>
        <button @click="value += 5">Add 5</button>
        <button @click="value += 1">Add 1</button>
        <p>{{ result }}</p>
    </div>
    <!-- 2) Watch for changes in the "result" and reset the "value" after 5 seconds (hint: setTimeout(..., 5000) -->
    <div>
        <label for="timeout"> Manuelle Eingabe des Timeout</label><br>
        <input name="timeout" type="text" placeholder="after 5000ms" v-model="timeout">
        <p>{{ value }}</p>
    </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      value: 0,
      timeout: 2000
    };
  },
  computed: {
    result: function() {
      return this.value == 37 ? "done" : "not there yet";
    }
  },
  watch: {
    result: function() {
      var vm = this;
      setTimeout(function() {
        vm.value = 0;
      }, vm.timeout);
    }
  }
};
</script>

<style>
#app1 {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
