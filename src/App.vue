<script setup lang="ts">
import { ref } from 'vue';
import InputEx from './components/InputEx.vue';
import ButtonEx from './components/ButtonEx.vue';
import SwitchButton from './components/SwitchButton.vue';
import TableEx from './components/TableEx.vue';

const onClick = () => {
  alert('clicked!!');
};

const isActive = ref(false);
const switchToggle = () => {
  isActive.value = !isActive.value;
};

const header = ['1번 제목', '2번 제목'];
const rows = [
  [{ data: '1번 내용' }, { data: '2번 내용' }],
  [{ data: '1번 내용', colspan: 2 }],
];
</script>

<template>
  <InputEx />
  <hr />
  <ButtonEx value="커스텀 버튼 테스트" text-red background-black>
    <span>button</span>
  </ButtonEx>
  <ButtonEx type="submit" value="커스텀 버튼 테스트" sm>
    <span>submit</span>
  </ButtonEx>
  <ButtonEx type="reset" value="커스텀 버튼 테스트" lg pill text-green background-pink>
    <span>reset</span>
  </ButtonEx>
  <ButtonEx value="커스텀 버튼 테스트" md pill text-white background-navy @click.prevent="onClick">
    <span>클릭하면 알럿!</span>
  </ButtonEx>
  <hr />
  <SwitchButton :active="isActive" @click.prevent="switchToggle" />
  <hr />
  <TableEx :header="header" :rows="rows" />
</template>

