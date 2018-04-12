<template>
  <div id="app">
    <b-container fluid>
      <b-row>
        <b-col cols="12">
          <h1 class="display-2 text-center">Vue.js Tip Calculator</h1>
        </b-col>
      </b-row>
    </b-container>
    <b-container fluid>
      <b-row align-h="center" class="mt-5">
          <input v-model="tipInput" class="w-50" placeholder="Tip Percentage %" >
      </b-row>
      <b-row align-h="center" class="mt-5">
          <b-btn @click="lower" variant="danger">Lower</b-btn>
          <b-btn @click="raise" variant="success" class="ml-2">Higher</b-btn>
      </b-row>
    </b-container>
    <b-container fluid>
      <b-row align-h="center" class="mt-5">
        <input v-model="billInput" class="w-50" placeholder="Bill Total $">
      </b-row>
      <b-row align-h="center" class="mt-5">
        <b-btn @click="showTotal" size="lg" variant="success">Total</b-btn>
      </b-row>
    </b-container>
    <b-container>
      <b-row align-h="center" class="mt-3">
        <b-col cols="6">
          <b-jumbotron class="text-center mb-2 mt-0">
            {{ totalMsg }}
          </b-jumbotron>
        </b-col>
      </b-row>
    </b-container>
    <b-container>
      <b-row align-h="center">
        <b-btn @click="reset" size="sm" variant="dark" class="mb-2">Reset</b-btn>
      </b-row>
    </b-container>
  </div>
</template>
<script>
export default {
  name: "app",
  data() {
    return {
      totalMsg: "",
      tipInput: "20",
      billInput: ""
    };
  },
  methods: {
    showTotal: function() {
      var total = this.tipInput / 100 * this.billInput
      var roundedTotal = total.toFixed(2)
      this.totalMsg = "Your tip total is: " + "$" + roundedTotal
    },
    raise: function() {
      this.tipInput++
    },
    lower: function() {
      this.tipInput--
      if (this.tipInput <= 0) {
        alert("You can't put a negative tip amount. That'd be cruel!")
        this.tipInput = 0
      }
    },
    reset: function() {
      this.totalMsg = ""
      this.tipInput = ""
      this.billInput = ""
    }
  }
};
</script>