<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import { Prop } from "vue-property-decorator";

@Component
export default class Action extends Vue {
  @Prop()
  label!: string;

  @Prop({ default: "button" })
  appereance!: string;

  onClick() {
    this.$emit("click");
  }
}
</script>
<template>
  <button class="light-action light" :class="appereance" @click="onClick">
    <slot name="prepend" />
    <slot>{{ label }}</slot>
    <slot name="append" />
  </button>
</template>
<style lang="scss" scoped>
.light {
  &-action {
    border-radius: 2px;
    padding: 3px;
    &.button {
      border: solid thin #ccc;
      background: linear-gradient(to top, #ece9e6, #ffffff);
    }

    &.on {
      background: linear-gradient(to top, #cccccc, #efefef);
    }
  }
}
</style>
