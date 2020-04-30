<template>
  
    <div id="addblog">
        <div v-if="!submitted">
          <h2>Add to the Blog</h2>
          <label >Blog Title:</label>
          <input type="text" required v-model.lazy="Blog.title">
          <label >Blog Content:</label>
          <textarea v-model.lazy="Blog.content"></textarea>
          <div id="checkboxes">
              <h3>Select Your favorite framework</h3>
              <label>Vuetify</label>
              <input type="checkbox" value='vuetify' v-model="Blog.frameworks">
              <label>React</label>
              <input type="checkbox" value='React' v-model="Blog.frameworks">
              <label>Angular</label>
              <input type="checkbox" value='Angular' v-model="Blog.frameworks">
              <label>Node</label>
              <input type="checkbox" value='Node' v-model="Blog.frameworks">
          </div>
          <h3>Authors</h3>
          <select v-model="Blog.author"> 
              <option v-for="author in authors" :key="author.key">{{ author }}</option>
          </select>
          <button v-on:click="submit" >Submit blog</button>
        </div>
          

          <div id="Preview">
              <h1 v-if="submitted = submitted">Thank You for adding to this blog</h1>
              <h2>Blog Preview</h2>
              <h3>Blog title:</h3>
              <p>{{ Blog.title }}</p>
              <h3>Blog content:</h3>
              <p>{{ Blog.content }}</p>
              <h3>Categories:</h3>
              <ul >
                  <li v-for="frame in Blog.frameworks" :key="frame.key">{{frame}}</li>
              </ul>
              <h3>Author:</h3>
              <p>{{ Blog.author }}</p>
          </div>
    </div>
      
 
</template>

<script>


export default {
 
  data(){
    return {
      Blog : {
          title : '',
          content : '',
          frameworks : [],
          author: ''
      },
      authors: ['Lekan', 'olawale', 'ibraheem', 'medaz'],
      submitted : false
      
    }
  },
  methods:{
      submit: function(){
          this.submitted = true
      }
  }
}
</script>

<style scoped>
    #addblog{
        max-width:650px;
        margin: 0 auto !important;
        padding:40px;
        background:teal;
        
    }
    h2{
        font-size:30px;
        color:white;
    }
    label{
        display: block;
        font-size:20px;
        padding-top:15px;
        color:white;
    }
    input[type=text], textarea{
        width:100%;
        padding:8px;
    }
    
    #Preview{
        padding:10px 20px;
        border:1px dotted #ccc;
        margin:30px 0;
        color:white;
    }
    #Preview p {
        font-size: 15px;
        
    }
    h3{
        color:white;
    }
    
    #checkboxes label{
        font-size:20px;
        display:inline-block;
        color:white;
        
    }
    #checkboxes input{
        margin-right:10px;
    }
    button{
        display:block;
        margin-top:20px;
        padding:10px;
    }
    body{
        background:teal;
    }
</style>
