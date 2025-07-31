<script setup>
import { ref } from 'vue';

const items = ref(
  [
    { id: Math.random(), name: '珍珠奶茶', desc: `香濃奶茶搭配QQ珍珠!`, price: 10, amount: 3 },
    { id: Math.random(), name: '冬瓜檸檬', desc: `清新冬瓜配上新鮮檸檬!`, price: 20, amount: 3 },
    { id: Math.random(), name: '翡翠檸檬', desc: `綠茶與檸檬的完美結合!`, price: 30, amount: 3 },
    { id: Math.random(), name: '四季春茶', desc: `香醇四季春茶，回甘無比!`, price: 50, amount: 3 },
    { id: Math.random(), name: '阿薩姆奶茶', desc: `阿薩姆紅茶搭配香醇鮮奶!`, price: 50, amount: 3 },
    { id: Math.random(), name: '檸檬冰茶', desc: `檸檬與冰茶的清新組合!`, price: 60, amount: 3 },
    { id: Math.random(), name: '芒果綠茶', desc: `芒果與綠茶的獨特風味!`, price: 70, amount: 3 },
    { id: Math.random(), name: '抹茶拿鐵', desc: `抹茶與鮮奶的絕配!`, price: 80, amount: 3 }
  ]
);

const editIdx = ref(0);
const editName = ref(``);

function addItem(item, _add = true) {
  if (_add) {
    item.amount++;
  } else {
    if (item.amount <= 0) {
      return;
    }
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
  let promptText = prompt('請輸入新的品項名稱', item.name);
  // item.name = prompt('請輸入新的品項名稱', item.name);
  console.log(promptText);
  item.name = promptText ? promptText : item.name;
}

function startEditName(item) {
  editIdx.value = item.id;
  editName.value = item.name;
}

function comfirmEdit() {
  editIdx.value = 0;
}

</script>

<template>
  <table>
    <thead>
      <th scope="col">品項</th>
      <th scope="col">描述</th>
      <th scope="col">價格</th>
      <th scope="col">庫存</th>
      <th scope="col">更改</th>
    </thead>
    <tbody>
      <tr v-for="(item, index) in items" :key="index">

        <td v-if="editIdx !== item.id" v-on:click="startEditName(item)">
          {{ item.name }}
        </td>
        <td v-else>
          <input type="text" v-model="item.name">
          </input>
        </td>

        <td>{{ item.desc }}</td>
        <td>{{ item.price }}</td>
        <td>
          <button v-on:click="addItem(item, false)">-</button>
          {{ item.amount }}
          <button v-on:click="addItem(item)">+</button>
        </td>

        <td v-if="editIdx !== item.id">
          <button v-on:click="startEditName(item)">編輯</button>
        </td>
        <td v-else>
          <button v-on:click="comfirmEdit(item)">確定</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<style></style>