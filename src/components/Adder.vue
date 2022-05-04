<script setup>
import { ref } from 'vue';

const sum = ref(0);
const increase = ref('1');

const add = () => {
  const parsed = parseInt(increase.value);
  if (isNaN(parsed)) {
    alert('増加量には数字を入力してください');
  } else if (parsed < 0) {
    alert('増加量には0以上の値を入力してください');
  } else {
    sum.value += parsed;
  }
};

const reset = () => {
  sum.value = 0;
};

const changeIncrease = (e) => {
  const value = e.target.value;
  const parsed = parseInt(value);
  // 空文字か0以上の数字のみ入力可
  if (value === '' || (!isNaN(parsed) && parsed >= 0)) {
    increase.value = value;
  } else {
    alert('0以上の数字を入力してください');
  }
};
</script>

<template>
  <div class="adder">
    <h2>合計：{{sum}}</h2>
    <p>増加量：<input type="number" :value="increase" @input="changeIncrease"/></p>
    <button @click="add">足す</button>
    <button @click="reset">リセット</button>
  </div>
</template>