<template>
  <Layout>
    <h1> {{ $page.post.title }} </h1>
    <g-image
      alt="Blog Image"
      :src="$page.post.fields.img"
      width="200px"
    />
  </Layout>
</template>

<page-query>
query($path : String!) {
post: redditPost(path: $path){
  title,
  fields {
    img
  }
}
}
</page-query>

<script >

export default {
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  }
}
</script>