<template>
 <Layout>
  <!-- Page Header -->
  <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
    <div class="overlay"></div>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div class="site-heading">
            <h1>Clean Blog</h1>
            <span class="subheading">A Blog Theme by Start Bootstrap</span>
          </div>
        </div>
      </div>
    </div>
  </header>
  <!-- Main Content -->
  <div class="container">
    <div class="row">
      <div class="col-lg-8 col-md-10 mx-auto">
        <div class="post-preview" v-for="p in postData" :key="p.id">
          <g-link :to="'/post/'+p.id">
            <h2 class="post-title">
             {{p.title}}
            </h2>
            <h3 class="post-subtitle">
              {{p.content}}
            </h3>
          </g-link>
          <p class="post-meta">Posted by
            <a href="#" v-for="t in p.tags" :key="t.id">{{t.title}} </a> 
            {{p.created_at}}</p>
        </div>
        <hr>
       
        <!-- Pager -->
        <div class="clearfix">
          <a class="btn btn-primary float-right" href="#">Older Posts &rarr;</a>
        </div>
      </div>
    </div>
  </div>
 </Layout>
</template>

<script>
import axios from 'axios'
export default {
  name:'HomePage',
  metaInfo: {
    title: 'Hello, world!'
  },
   data(){
    return {
      postData:[]
    }
  },
  mounted(){
    console.log('mounted');
    axios.get(`http://localhost:1337/posts`).then(res=>{
      console.log(res.data);
      this.postData = res.data;
    })
  }
}
</script>

<style>

</style>
