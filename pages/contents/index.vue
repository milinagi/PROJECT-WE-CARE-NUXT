<template>
  <v-container v-if="contents">
    <v-row>
      <v-col v-for="(content, idx) in contents" :key="idx" sm="6" lg="4">
        <ContentCard :content="content" height="300" class="elevation-5" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  async asyncData({$axios}) {
    const contents = await $axios.$get('/content')
    return {
      contents
    }
  },
};
</script>
