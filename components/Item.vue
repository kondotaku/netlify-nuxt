<template>
  <div class="item">
    <div>ID: {{id}}</div>
    <div>名前: {{txt}}</div>
    <div>値段: {{desc}}</div>
  </div>
</template>

<script>
export default {
  name: "ItemDetail",
  props: {
    id: String,
    txt: String,
    desc: String
  }
};
</script>