<script setup lang="ts">
import { ref, onMounted, useAttrs } from 'vue';

type TButton = 'button' | 'submit' | 'reset';
interface IButton {
  type? : TButton,
  sm?: boolean,
  md?: boolean,
  lg?: boolean,
  pill?: boolean,
  value?: string,
}

const props = withDefaults(defineProps<IButton>(), {
  type: 'button',
});
const attrs = useAttrs();
const btn = ref();
const classes: string[] = [];

if (props.sm) {
  classes.push('sm');
} else if (props.lg) {
  classes.push('lg');
} else {
  classes.push('md');
}

if(props.pill) {
  classes.push('pill');
}


onMounted(() => {
  Object.keys(attrs).forEach((attr) => {
    if (attr.startsWith('text-')) {
      btn.value.style.color = attr.substring(5);
    }

    if (attr.startsWith('background-')) {
      btn.value.style.backgroundColor = attr.substring(11);
    }
  })
});

</script>

<template>
  <button v-bind="attrs" :type="type" :class="classes" ref="btn">
    {{props.value}}
    <slot></slot>
  </button>
</template>

<style scoped>
button {
  outline: none;
}

.sm {
  height: 20px;
  font-size: 13px;
}

.md {
  height: 30px;
  font-size: 22px;
}

.lg {
  height: 40px;
  font-size: 31px;
}

.pill {
  border-radius: 16px;
}

</style>