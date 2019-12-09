<template>
  <div class="hello">
    <div class="field" v-for="(record, index) in records" :key="record.id">
      <div class="control name">
        <label class="radio">
          <input type="radio" v-model="pickedProduct" :value="index" :id="record.id" :name="record.id" />
          {{ record.name }}
        </label>
      </div>
      <span class="price">${{ record.price }} per license</span>
    </div>
    <div class="divider" />
    <div class="field combo-control">
      <label for="count-select">Number of licenses:</label>
      <div class="control select" id="count-select">
        <select v-model="pickedCount">
          <option :value="1">1</option>
          <option :value="2">2</option>
          <option :value="3">3</option>
          <option :value="4">4</option>
          <option :value="5">5</option>
          <option :value="6">6</option>
          <option :value="7">7</option>
          <option :value="8">8</option>
          <option :value="9">9</option>
          <option :value="10">10</option>
        </select>
      </div>
    </div>
    <div class="divider" />
    <div style="padding-top: 10px">Total: <span class="has-text-info">${{ getAmount }}</span></div>
    <div class="has-text-centered" style="padding-top: 10px">
      <button class="button is-success is-rounded">Buy Now</button>
    </div>
    <div class="has-text-info" style="padding-top: 10px">Selected plan: #{{ pickedProduct + 1 }}</div>
  </div>
</template>

<script>
import json from '../assets/data.json'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      records: json,
      pickedProduct: 0,
      pickedCount: 10
    }
  },
  computed: {
    getAmount: function() {
      return this.records[this.pickedProduct].price * this.pickedCount;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.name {
  display: inline-block;
  width: 250px;
}
.divider {
  width: 100%;
  height: 1px;
  background-color: rgba(0, 0, 0, 0.5);
}
.combo-control {
  padding-top: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
