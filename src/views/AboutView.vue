<template>
  <div class="about">
    <h1>This is an about page</h1>
    counter:{{ counter }}
    <button @click="plus_counter()">click</button>
    <p>{{ my_profile }}</p>
    <div>my_name is {{ `${my_profile.firstName} ${my_profile.lastName}` }}</div>
    <div>username is {{ `${user.firstName} ${user.lastName}` }}</div>
    {{ fillName }}

    <!-- component file -->
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

import { reactive, computed } from "vue";

const counter = ref(0);
const plus_counter = () => {
  counter.value++;
};
// 関数自体に戻り値が存在する時、
// const plus_counter = (): number => {
//   return counter.value++;
// };

// 関数内で引数を指定する時、
// <button @click="plus_counter(1)">click</button>
// const plus_counter = (count: number): number => {
//   return (counter.value += count);
// };

// interface User {}
type User = {
  firstName: string;
  lastName: string;
  age: number;
};
const user = reactive({} as User);

user.firstName = "John";
user.lastName = "Nasayosi";
const my_profile: User = reactive({
  firstName: "Oga",
  lastName: "Haya",
  age: 23,
});

const fillName = computed(() => `${user.firstName} ${user.lastName}`);
</script>
