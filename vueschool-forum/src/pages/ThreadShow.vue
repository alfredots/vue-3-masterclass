<template>
  <div class="col-large push-top">
    <h1>{{ thread.title }}</h1>

    <post-list :posts="threadPosts"/>

    <post-editor @save-post="savePost"/>
  </div>
</template>

<script>
import sourceData from '@/data.json'
import PostList from '@/components/PostList'
import PostEditor from '@/components/PostEditor'

export default {
  name: 'ThreadShow',
  components: {
    PostList,
    PostEditor
  },
  props: {
    id: {
      required: true,
      type: String
    }
  },
  data () {
    return {
      threads: sourceData.threads,
      posts: sourceData.posts
    }
  },
  computed: {
    thread () {
      return this.threads.find(thread => thread.id === this.$route.params.id)
    },
    threadPosts () {
      return this.posts.filter(post => post.threadId === this.id)
    }
  },
  methods: {
    savePost (eventData) {
      const post = {
        ...eventData.post,
        threadId: this.id
      }
      this.posts.push(post)
      this.threads.posts.push(post.id)
    }
  }
}
</script>

<style scoped>
.profile-card {
    padding: 10px 20px 20px 20px;
    margin-bottom: 10px;
    background: white;
    box-shadow: 2px 2px 1px rgba(136, 136, 136, 0.09);
    align-self: self-end;
}

@media (min-width: 820px) {
    .profile-card {
        margin-right: 20px;
    }
}

.profile-card .title {
    word-break: break-all;
}

.profile-card .stats {
    display: flex;
    margin: 20px 0px;
}

.profile-card .stats span {
    flex-basis: 50%;
}

.profile-card .user-website {
    display: flex;
    justify-content: center;
    align-items: baseline;
}

.profile-header {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    padding: 0 0px;
}

@media (max-width: 720px) {
    .profile-header {
        flex-wrap: wrap;
    }
}
</style>
