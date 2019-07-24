<template>
  <Layout :showFooter= "true">
    
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <div style="text-align:center;">
      <g-image alt="Example image" src="~/assets/images/Profile.png" height="200" width="200" fit="cover"/>
      <h1>Chongwen Li</h1>

    </div>
    
   
    <p>
      Newly graduated computer science master student. Learning new technology and improving everyday
    </p>

    <p class="home-links">
      <a href="https://github.com/LiChongWen" target="_blank" rel="noopener">My GitHub</a>
    </p>
    <!-- <Footer></Footer> -->
  </Layout>
</template>

<script>
import Footer from "~/components/Footer.vue"

export default {
  metaInfo: {
    title: 'My Blog'
  },
  components: {
    Footer
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
.home-links {
  text-align: center;
}
</style>
