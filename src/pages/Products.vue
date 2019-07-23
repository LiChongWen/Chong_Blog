<template>
    <Layout>
        <h1>Products</h1>
        <div style="text-align: center" v-for="edge in $page.allContentfulProduct.edges" :key="edge.node.id">
            <h2 style="margin-bottom: 0.25em;">{{edge.node.name}}</h2>
            <span>$ {{edge.node.price}}</span>
            <g-image :src="edge.node.image.file.url" style="width: 100%; height: 300px; object-fit: contain;" :alt="edge.node.image.title"/>
            <p>
                {{edge.node.description}}
            </p>
        </div>
        <Pager :info="$page.allContentfulProduct.pageInfo" linkClass="pager"/>
    </Layout>
</template>

<page-query>
query ($page: Int) {
  allContentfulProduct (perPage: 3, page: $page) @paginate {
    pageInfo {
        currentPage
        totalPages
    }
    edges {
      node {
        id
        path
        name
        price
        description
        image {
          title
          file {
            url
          }
        }
      }
    }
  }
}
</page-query>

<script>
import {Pager} from 'gridsome'
export default {
    components: {Pager},
    metaInfo: {
        title: "Products",
        meta : [
            {charset: 'utf-8'},
            {name: 'author', content: "Chongwen Li"},
            {name: "description", content: "Luxury apparel, shoes and accessories"},
            {name: "keywords", content: "Premium Jackets, High-End Clothing"}
        ]
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
