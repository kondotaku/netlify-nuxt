<template>
  <div class>
    <div class="ttl py-5">
      <h1 class="h1 text-center">{{ title }}</h1>
    </div>
    <div class="d-flex flex-wrap picture-container">
      <div v-for="item in items" :key="item" class="col-md-4 col-6 p-3 mb-4">
        <div class="picture text-center mb-2">
          <!-- picture_imgを取得する -->
          <img :src="item.gazo.url" class="img-thumbnail img-fluid img_wrap" />
        </div>
        <!-- picture_dateを取得する -->
        <p class="date mb-0 font-weight-bold" v-html="item.dat" />
        <h2 class="h3 text-primary">
          <!-- picture_areaを取得する -->
          {{ item.txt }}
        </h2>
        <p>{{ item.desc }}</p>
      </div>
    </div>
    <div class="footer bg-success py-5">
      <p class="text-center text-white">Copyright &copy; picture All Rights Reserved.</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      items: "",
      title: "want itemlist"
    };
  },
  head: {
    script: []
  },
  head() {
    return {
      title: this.title,
      meta: [
        {
          hid: "description",
          name: "これは僕のほしいアイテムのリスト",
          content: "dこれは僕のほしいアイテムのリストです"
        }
      ]
    };
  },

  async asyncData() {
    const { data } = await axios.get(
      "https://kondodev.microcms.io/api/v1/postimage",
      {
        headers: { "X-API-kEY": "6a4db142-5fed-4ded-b1ff-fb497a35eae6" }
      }
    );
    console.log(data);

    return {
      items: data.contents
    };
  }
};
</script>

<style>
.picture-container {
  max-width: 1100px;
  margin-left: auto;
  margin-right: auto;
}
.img_wrap {
  object-fit: cover;
  height: 300px;
}
</style>
