<template>
  <div class="container">
    <div class="col-full push-top">
      <ul class="breadcrumbs">
        <li><a href="/index.html"><i class="fa fa-home fa-btn"></i>Home</a></li>
        <li><a href="/category.html">Discussions</a></li>
        <li class="active"><a href="#">Cooking</a></li>
      </ul>

      <div class="forum-header">
        <div class="forum-details">
          <h1>Cooking</h1>
          <p class="text-lead">Discuss your passion for food and cooking</p>
        </div>
        <a href="new-thread.html" class="btn-green btn-small">Start a thread</a>
      </div>
    </div>

    <div class="col-full">

      <thread-list :threads="threads"/>

    </div>

  </div>
</template>

<script>
import ThreadList from '@/components/ThreadList'
import sourceData from '@/data.json'

export default {
  name: 'Forum',
  components: { ThreadList },
  props: {
    id: {
      required: true,
      type: String
    }
  },
  computed: {
    forum () {
      return sourceData.forums.find(forum => forum.id === this.id)
    },
    threads () {
      return sourceData.threads.filter(thread => thread.forumId === this.id)
    }
  }
}
</script>

<style scoped>

</style>
