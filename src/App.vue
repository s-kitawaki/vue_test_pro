<template>
  <v-app>
    <v-main>
      <HelloWorld/>
      <h1 style="color:red;">Kitawakiが追加しました。</h1>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
}
</script>
