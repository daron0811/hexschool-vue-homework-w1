<script setup>
import { ref } from 'vue';

const item = ref(
  [
    { id: Math.random, name: '珍珠奶茶', desc: 90, price: 50, amount: 3 },
    { id: Math.random, name: '冬瓜檸檬', desc: 85, price: 50, amount: 3 },
    { id: Math.random, name: '翡翠檸檬', desc: 78, price: 50, amount: 3 },
    { id: Math.random, name: '四季春茶', desc: 92, price: 50, amount: 3 },
    { id: Math.random, name: '阿薩姆奶茶', desc: 85, price: 50, amount: 3 },
    { id: Math.random, name: '檸檬冰茶', desc: 78, price: 50, amount: 3 },
    { id: Math.random, name: '芒果綠茶', desc: 92, price: 50, amount: 3 },
    { id: Math.random, name: '抹茶拿鐵', desc: 85, price: 50, amount: 3 }
  ]
);

function addItem(item, _add = true) {
  if (_add) {
    item.amount++;
  } else {
    if (item.amount <= 0)
      return;
    item.amount--;
  }
}

function resetName(item) {
  /*
  //TODO:做空值檢查
  let promptText = prompt('請輸入新的品項名稱', item.name);
  console.log(promptText);
  if (promptText === null) {
    alert('品項名稱不能為空');
    return;
  }
  item.name = promptText;*/
  item.name = prompt('請輸入新的品項名稱', item.name);
}

</script>

<template>
  <table>
    <thead>
      <th scope="col">品項</th>
      <th scope="col">描述</th>
      <th scope="col">價格</th>
      <th scope="col">庫存</th>
    </thead>
    <tbody>
      <tr v-for="(i, index) in item" :key="index">
        <td>{{ i.name }}</td>
        <td>{{ i.desc }}</td>
        <td>{{ i.price }}</td>
        <td><button v-on:click="addItem(index, false)">-</button>{{ i.amount }}<button
            v-on:click="addItem(i)">+</button>
        </td>
        <td><button v-on:click="resetName(index)">編輯</button></td>
      </tr>
    </tbody>
  </table>
</template>
<style></style>