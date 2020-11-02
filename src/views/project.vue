<template>
  <div>
    <input type="text" v-model="inputVal" @change="setVal" />
    <ComOne :ComOneData="ComOneData" :ComOneDataTwo="ComOneDataTwo"> </ComOne>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
import ComOne from "./attr/ComOne.vue";

@Component({ components: { ComOne } })
export default class Home extends Vue {
  private ComOneData = {
    one: 121,
    two: 65464
  };

  private ComOneDataTwo = {
    one: 121,
    two: 65464
  };

  private setVal() {
    this.ComOneData.one = Date.now();
    this.ComOneData.two = Date.now();

    this.ComOneDataTwo.one = Date.now();
    this.ComOneDataTwo.two = Date.now();
    this.ComOneDataTwo.onetwo = Date.now();
  }

  private inputVal = "21";
}
</script>
