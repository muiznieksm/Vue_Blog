<template>
  <div v-if="error">{{ error }}</div>
  <div v-if="post" class="post">
    <h3>{{ post.title }}</h3>
    <p class="pre">{{ post.body }}</p>
    <span v-for="tag in post.tags" class="pill">#{{ tag }}</span>
  </div>
  <div v-else><Spiner /></div>
</template>

<script>
import getPost from "../composable/getPost";
import Spiner from "../components/Spiner.vue";
import { useRoute } from "vue-router";

export default {
  props: ["id"],
  components: { Spiner },
  setup(props) {
    const route = useRoute();

    const { post, error, load } = getPost(route.params.id);
    load();
    return { post, error };
  },
};
</script>

<style>
.tags a {
  margin-right: 10px;
}
.post {
  max-width: 1200px;
  margin: 0 auto;
}
.post p {
  color: #444;
  line-height: 1.5em;
  margin-top: 40px;
}
.pre {
  white-space: pre-wrap;
}
.pill {
  display: inline-block;
  margin: 10px 10px 0 0;
  color: #444;
  background: #ddd;
  padding: 8px;
  border-radius: 20px;
  font-size: 14px;
}
</style>
