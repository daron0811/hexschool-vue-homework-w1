<script setup>
import { ref } from 'vue';
const a = ref(2); // 使用ref去做響應式動態更新

function showValue() {
  alert(`你輸入的是${a.value}`);
}

const students = ref([
  { id: 's001', name: '洧杰', score: 90 },
  { id: 's002', name: '小花', score: 85 },
  { id: 's003', name: '阿明', score: 78 },
  { id: 's004', name: '佩佩', score: 92 }
])

</script>

<template>
  <input type="text" v-bind:value="a"></input> <!-- v-bind 僅讀取值  文字輸入欄位輸入預設值-->
  <input type="text" v-model="a"> </input><!-- v-model 雙向綁定 -->
  <input type="text" v-model="a"> </input><!-- v-model 雙向綁定 -->
  <h1>{{ a }}</h1>
  <h1>{{ a }}</h1>
  <h1>{{ a }}</h1>
  <h1>{{ a }}</h1>
  <button v-on:click="a++">點我+1</button>"
  <button v-on:click="showValue(a)">點我</button>"

  <li v-for="student in students" :key="student.id" class="mb-2 p-2 border rounded">
    <p>🆔 學號：{{ student.id }}</p>
    <p>📛 姓名：{{ student.name }}</p>
    <p>📈 分數：{{ student.score }}</p>
  </li>
</template>
<style></style>