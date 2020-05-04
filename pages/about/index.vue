<template>
  <div class>
    <div class="ttl py-5">
      <h1 class="h1 text-center">{{ item.title }}</h1>
    </div>
    <div class="d-flex flex-wrap picture-container">
      <div class="picture text-center mb-2">
        <!-- picture_imgを取得する -->
        <img :src="item.gazo.url" class="img-thumbnail img-fluid img_wrap" />
      </div>
      <!-- picture_dateを取得する -->
      <div v-html="item.desc" class="pl-0 pl-md-5"></div>
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
      item: ""
    };
  },
  async asyncData() {
    const { data } = await axios.get(
      "https://kondodev.microcms.io/api/v1/about",
      {
        headers: { "X-API-kEY": "6a4db142-5fed-4ded-b1ff-fb497a35eae6" }
      }
    );
    console.log(data);

    return {
      item: data,
      title: data.title
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
          name: "このサイトについて",
          content: "このサイトを作った理由などを記載します"
        }
      ]
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
