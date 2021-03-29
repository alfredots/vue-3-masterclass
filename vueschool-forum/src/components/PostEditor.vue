<template>
  <div class="col-full push-top">

    <h1>Create new thread in <i>Cooking</i></h1>

    <form @submit.prevent="addPost">
      <div class="form-group">
        <label for="thread_title">Title:</label>
        <input type="text" id="thread_title" class="form-input" name="title" >
      </div>

      <div class="form-group">
        <label for="thread_content">Content:</label>
        <textarea v-model="newPostText" id="thread_content" class="form-input" name="content" rows="8" cols="140"></textarea>
      </div>

      <div class="btn-group">
        <button class="btn btn-ghost">Cancel</button>
        <button class="btn btn-blue" type="submit" name="Publish">Publish </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newPostText: ''
    }
  },
  methods: {
    addPost () {
      const postId = 'gggg' + Math.random()
      const post = {
        id: postId,
        text: this.newPostText,
        publishedAt: Math.floor(Date.now() / 1000),
        userId: 'VXjpr2WHa8Ux4Bnggym8QFLdv5C3'
      }
      this.newPostText = ''
      this.$emit('save-post', { post })
    }
  }
}
</script>

<style>

</style>
