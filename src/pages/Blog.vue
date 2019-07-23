<template>
    <Layout>
        <h1>Blog</h1>
        <article v-for="edge in $page.allPost.edges" :key="edge.node.id" style="margin-bottom: 2em;">
            <g-image :src="edge.node.cover_image" style="width: 100%"/>
           <h2>{{edge.node.title}}</h2>
           <p>{{edge.node.excerpt}}</p>
           <p>Posted {{edge.node.date}} - {{edge.node.timeToRead}} min read</p>
            <div>
                <g-link style="padding-right: .25em" v-for="tag in edge.node.tags" :to="tag.path" :key="tag.id">#{{tag.id}}</g-link>
            </div>
            <g-link :to="edge.node.path">Read more</g-link>
            <!-- <div v-html="edge.node.excerpt">
            </div> -->
            <hr style="border: 0; height: 0; border-top: 1px solid rgba(0, 0, 0, 0.1); border-bottom: 1px solid rgba(255, 255, 255, 0.3);">
        </article>
        <Pager :info="$page.allPost.pageInfo" linkClass="pager"/>
    </Layout>
</template>


<page-query>
query ($page: Int) {
  allPost (perPage: 3, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges{
      node {
        id
        title
        excerpt
        date (format: "MMMM Do, YYYY")
        tags{
            id
            path
        }
        timeToRead
        path
        cover_image (width: 1000, height: 300, fit: cover, quality: 100, blur: 50)
      }
    }
  }
}
</page-query>

<script>
import {Pager} from 'gridsome'
export default {
    components: {
        Pager
    }
}
</script>

<style>
.pager {
    font-size: 1.5rem;
    letter-spacing: 0.5px;
    padding: 40px 20px;
}
</style>
