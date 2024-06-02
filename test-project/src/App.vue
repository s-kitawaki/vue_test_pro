<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

import { ref, watch} from 'vue'

// リアクティブな状態を定義
const msg = ref('')
const isChecked = ref(false)
const isZero = 0

const isNumber = ref(isZero)

isNumber.value = 1; // この変更が検知され、watchのコールバックが実行される
isNumber.value = 2;

// isCheckedの変化を監視してmsgを更新
watch(isChecked, (newValue) => {
  msg.value = newValue ? 'Hello World!' : 'Bey World!'
})

// テーブルデータ
const headers = ref([
  { text: 'Name', value: 'name' },
  { text: 'Age', value: 'age' },
  { text: 'Occupation', value: 'occupation' }
]);

const items = ref([
  { name: 'John Doe', age: 30, occupation: 'Engineer' },
  { name: 'Jane Smith', age: 25, occupation: 'Designer' },
  { name: 'Sam Brown', age: 22, occupation: 'Developer' }
]);
</script>

<template>
  <v-app>
    <v-container>

  <header>
    <!-- <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" /> -->
<v-img
          alt="Vue logo"
          class="logo"
          src="@/assets/logo.svg"
          width="125"
          height="125"
        ></v-img>

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
      <!-- チェックボックスを追加 -->
      <!-- <label>
        <input type="checkbox" v-model="isChecked" /> Toggle Message
      </label> -->
      <v-checkbox
            v-model="isChecked"
            label="Toggle Message"
          ></v-checkbox>
      <p>{{msg}}</p>
    </div>
  </header>

      <!-- Vuetifyのテーブルコンポーネント -->
      <v-data-table
        :headers="headers"
        :items="items"
        class="elevation-1"
      ></v-data-table>

  <RouterView />
    </v-container>
  </v-app>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
