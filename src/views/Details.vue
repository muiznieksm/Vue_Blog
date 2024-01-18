<template>
  <div v-if="error">{{ error }}</div>
  <div v-if="post" class="post">
    <h3>{{ post.title }}</h3>
    <p class="pre">{{ post.body }}</p>
    <span v-for="tag in post.tags" class="pill">#{{ tag }}</span>
    <button @click="handleDelete">Delete</button>
  </div>
  <div v-else><Spinner /></div>
</template>

<script>
import getPost from "../composables/getPost";
import Spinner from '../components/Spinner.vue'
import { useRoute, useRouter } from "vue-router";

export default {
  props: ["id"],
  components: { Spinner },
  setup(props) {
    const router = useRouter();
    const route = useRoute();

    const { post, error, load } = getPost(route.params.id);
    load();

const handleDelete = (post) => {
fetch(`http://localhost:3000/posts/${route.params.id}`, {
  method: 'DELETE',
  headers: {'Content-Type': 'application/json'},
  body: JSON.stringify(post)
})
  .then(router.push('/'))
  .catch(error => console.log(error))
}


    return { post, error, handleDelete};
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
