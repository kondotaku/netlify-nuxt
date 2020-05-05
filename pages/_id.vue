//pages/careers/_id.vue
<template>
  <div>
    <h2>キャリア</h2>
    <div v-for="(item, index) in items" :key="index">
      <nuxt-link :to="'posts/' + item.id">
        <h2>{{ item.title }}</h2>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      items: ""
    };
  },

  async asyncData({ params }) {
    const { data } = await axios.get(
      "https://kondodev.microcms.io/api/v1/postimage",
      {
        headers: { "X-API-kEY": "6a4db142-5fed-4ded-b1ff-fb497a35eae6" }
      }
    );

    return {
      items: data.contents
    };
  }
};
</script>
