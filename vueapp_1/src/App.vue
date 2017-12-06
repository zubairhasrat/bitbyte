<template>
  <div id="app" class="container">
    <div class="page-header">
      Vue js  2 and firebase based mini app
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">
        <h1>Add Books</h1>
      </div>
      <div class="panel-body">
        <form id="form" class="form-inline" v-on:submit.prevent="addBook">
          <div class="form-group">
            <label for="bookTitle">Title</label>
            <input type="text" id="bookTitle" class="form-control" v-model="newBook.title">
          </div>
          
          <div class="form-group">
            <label for="bookAuthor">Author</label>
            <input type="text" id="bookAuthor" class="form-control" v-model="newBook.author">
          </div>
          <div class="form-group">
            <label for="url">Url</label>
            <input type="text" id="url" class="form-control" v-model="newBook.url">
          </div>
          <input type="submit" value="Add Book" class="btn btn-primary">
        </form>
      </div>
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">
        <h3>Books List</h3>
      </div>
      <div class="panel-body">
        <table class="table table-striped">
          <thead>
            <tr>
              <td>Title</td>
              <td>Author</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="book in books" :key="book.id">
              <td><a v-bind:href="book.url">{{book.title}}</a></td>
              <td>{{book.author}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

  </div>
</template>
<script>
import Firebase from 'firebase'
let config={
    apiKey: "AIzaSyCPrO07w9jdbLhGie-L8tzXIO-_EVkRElQ",
    authDomain: "vueapp-1.firebaseapp.com",
    databaseURL: "https://vueapp-1.firebaseio.com",
    projectId: "vueapp-1",
    storageBucket: "vueapp-1.appspot.com",
    messagingSenderId: "728993043751"
}
let app = Firebase.initializeApp(config);
let db = app.database();
let booksref = db.ref('books');

export default {
  name: 'app',
  firebase: {
    books: booksref
  },
  data() {
    return {
      newBook:{
          title :'',
          author :'',
          url :''
      }
    }
  },
  methods :{
    addBook : function(){
      booksref.push(this.newBook),
      this.newBook.title = '',
      this.newBook.author = '',
      this.newBook.url = ''
    }
  },
  mounted() {
    /*let $instance = this;
    booksref.on('value', function(snapshot) {
        $instance.books = [];
        snapshot.forEach(function(childSnapshot) {
          var temp = childSnapshot.val();
          temp.id = childSnapshot.ref.id;
          $instance.books.push(temp);
        });
    });*/
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
  color: #2c3e50;
  margin-top: 60px;
}
</style>
