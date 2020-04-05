<template>

<div class="container">
  <div class="row">
    <div class="col-sm-4">
      <h3>{{ item.webTitle}}</h3>
      <p>{{ item.sectionName }}</p>
      
    </div>
   <div class="col-sm-4">
    <h3>Publication Date</h3>
      <p>{{ item.pubDate }}</p>
      
    </div>
    <div class="col-sm-4">
       <h3>Web url</h3>    
      <p><a :href="item.webUrl">Click for link</a></p>
    </div>
   
  </div>
</div>
  
</template>

<script>
export default {
  name: "articleList",
  props: ["item"]
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
/* h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */
</style>
