<template>
  <section>
    <div class="home">33333333</div>
    <div class="home">33333333{{ JSON.stringify(ComOneData) }}</div>
    <div class="home">33333333{{ JSON.stringify(ComOneDataTwo) }}</div>
  </section>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
@Component({})
export default class Home extends Vue {
  @Prop()
  private ComOneData: any;

  @Prop()
  private ComOneDataTwo: any;

  private created() {
    console.log(this.ComOneData);
  }
}
</script>
