<template>
  <v-app>
    <v-main>
      <h1 style="color:red;">Kitawakiが追加しました。</h1>
      <HelloWorld/>
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
