<template>


<body id="top">
<!-- <div class="wrapper">
  <div id="header">
    <h1>The Guardian</h1>
    <p>Articles</p>
  </div> -->

  
      <div class="jumbotron text-center">
  <h1>The Guardian</h1>
  <h3>Articles</h3> 
       </div>

       

       

   <div class="well" >
   <div class="container">
  
  <form v-on:submit.prevent class="form-inline" action="/action_page.php">
    <div class="form-group">
      <label for="date_from">Date From: </label>
       <input v-model="dateFrom" type="date" class="form-control" id="date_from" >
    </div>
    <div class="form-group">
      <label for="date_to">Date To: </label>
      <input v-model="dateTo" type="date" class="form-control" id="date_to" >
    </div>

     <div class="form-group">
      <label for="searchTerm">Search Term: </label>
      <input v-model="searchTerm" type="input" class="form-control" id="searchTerm"  >
    </div>
    
    <button v-on:click="getFormData" type="submit" class="btn btn-default"> Submit</button>
  </form>
</div>
     </div>



    


  
<div class="container"> 

 

  

    <articleList  v-for="(item, index) in articleDetails" :key="index" :item="item"></articleList>
    <!-- <articleList  v-for="(item, index) in dummyList" :key="index" :item="item"></articleList> -->
  </div>

  </body>

</template>




<script>
import articleList from "./articleList.vue";
export default {
  components: {
    articleList
  },
  data() {
    return {
      dateFrom: "",
      dateTo: "",
      searchTerm: "",
      queryResults: "",
      articleDetails: [],
      dummyList:[
          {
              webTitle: "Boris Johnson's Brexit bill becomes law",
              webUrl: "https://www.theguardian.com/politics/2020/jan/23/boris-johnsons-brexit-bill-becomes-law"
,
              sectionName: "Politics",
              pubDate: "2020-01-23T17:06:58Z"
            },
            {
              webTitle: "Talking about Brexit the Mussolini way | Brief letters",
              webUrl: "https://www.theguardian.com/politics/2020/feb/07/talking-about-brexit-the-mussolini-way",
              sectionName: "Politics",
              pubDate: "2020-02-07T17:22:43Z"
            },
            {
              webTitle: "Brexit: MEPs ratify UK withdrawal agreement",

              webUrl: "https://www.theguardian.com/politics/2020/jan/29/brexit-meps-to-vote-on-withdr",
              sectionName: "Politics",
              pubDate: "2020-01-29T18:42:27Z"
            }
      ]
    };
  },
  methods: {
    getArticleData: function() {
      return fetch(
        "https://content.guardianapis.com/search?q=" +
          this.searchTerm +
          "&from-date=" +
          this.dateFrom +
          "&to-date=" +
          this.dateTo +
          "&format=json&api-key=test"
      )
        .then(answer => answer.json())
        .then(yuhu => yuhu.response.results)
        .then(results => {
          let resultRow;
          for (resultRow in results) {
            this.articleDetails.push({
              webTitle: results[resultRow].webTitle,
              webUrl: results[resultRow].webUrl,
              sectionName: results[resultRow].sectionName,
              pubDate: results[resultRow].webPublicationDate
            });
          }
        });
    },
    getFormData: function() {
      this.getArticleData();
      console.log(this.articleDetails);
    }
  }
};
</script>

<style>


 body{ 
    font-size:14px; 
font-family:Georgia, "Times New Roman", Times, serif;
 }

h1 {
    text-align: center;
    text-transform: uppercase; 
} 


 /* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
/* .form-inline {
  display: flex;
  margin: 0 -10px;
  justify-content: center;
} */
/* .form-item label {
  margin: 0 10px;
}

#push-right {
  margin: 0 20px;
}  */
</style>
