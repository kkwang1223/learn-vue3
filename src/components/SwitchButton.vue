<script setup lang="ts">
import { onUpdated } from 'vue';

interface IProps {
  type?: 'button' | 'reset' | 'submit';
  active?: boolean;
}
const props = withDefaults(defineProps<IProps>(), {
  type: 'button',
  active: false,
});

const classes: string[] = [];

const toggleClass = (isActive: boolean) => {
  if(isActive) {
    classes.push('deactive');
  } else {
    classes.pop();
  }
  return classes;
}
</script>

<template>
  <button :type="props.type" :class="toggleClass(props.active)">SWITCH</button>
</template>

<style scoped>
.deactive {
  filter: brightness(50%);
}
</style>