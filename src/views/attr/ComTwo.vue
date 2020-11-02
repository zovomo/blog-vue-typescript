<template>
  <div>
    <ComThree v-bind="$attrs"></ComThree>
    <div>2222{{ JSON.stringify(ComOneDataTwo) }}</div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import ComThree from "./ComThree.vue";
@Component({ components: { ComThree } })
export default class Home extends Vue {
  @Prop()
  private ComOneDataTwo: any;

  private created() {
    console.log(this.ComOneDataTwo);
  }
}
</script>
