<template>
  <ComTwo v-bind="$attrs"></ComTwo>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ComTwo from "./ComTwo.vue";
@Component({ components: { ComTwo } })
export default class Home extends Vue {}
</script>
