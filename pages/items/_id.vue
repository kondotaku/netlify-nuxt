//pages/careers/posts/_id.vue
<template>
  <div>
    <div class="picture text-center mb-2">
      <!-- picture_imgを取得する -->
      <img :src="item.gazo.url" class="img-thumbnail img-fluid img_wrap" />
    </div>
    <!-- picture_dateを取得する -->
    <time class="date mb-0 font-weight-bold date" v-html="item.dat">{{ item.dat }}</time>
    <nuxt-link
      class="badge-primary rounded-pill p-2"
      :to="'/items/category/' + item.relate.catID"
    >{{item.relate.cat}}</nuxt-link>

    <h2 class="h3 text-primary">
      <!-- picture_areaを取得する -->
      {{ item.txt }}
    </h2>
    <p>{{ item.desc }}</p>

    <nuxt-link to="/items/">一覧へ戻る</nuxt-link>
  </div>
</template>


<script>
import axios from "axios";

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://kondodev.microcms.io/api/v1/postimage/${params.id}`,
      {
        headers: { "X-API-KEY": "6a4db142-5fed-4ded-b1ff-fb497a35eae6" }
      }
    );
    return {
      item: data
    };
  },

  head: {
    script: []
  },
  head() {
    return {
      meta: [
        {
          hid: "description",
          name: "これは僕のほしいアイテムのリスト",
          content: "dこれは僕のほしいアイテムのリストです"
        }
      ]
    };
    console.log("testing");
  }
};
</script>
