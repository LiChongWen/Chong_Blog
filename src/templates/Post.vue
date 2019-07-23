<template>
    <Layout>
        <div v-html="$page.post.content"></div>
        <vue-disqus shortname="chongblog-1" :identifier="$page.post.id"></vue-disqus>
    </Layout>
</template>

<page-query>
query ($path: String!) {
  post(path: $path) {
    id
    content
  }
}
</page-query>
