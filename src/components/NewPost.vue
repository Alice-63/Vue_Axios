<template>
  <div class="container pt-5">
    <h3>Yazı Ekle</h3>
    <hr>
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <label>Yazar</label>
        <input v-model="post.author" type="text" class="form-control" placeholder="Yazar adını giriniz...">
      </div>
      <div class="form-group">
        <label>Başlık</label>
        <input v-model="post.title" type="text" class="form-control" placeholder="Yazının başlığını giriniz...">
      </div>
      <div class="form-group">
        <label>Görsel Bağlantısı</label>
        <input v-model="post.thumbnail" type="text" class="form-control" placeholder="Yazının görselini giriniz...">
      </div>
      <div class="form-group">
        <label>Önizleme Metni</label>
        <input v-model="post.previewText" type="text" class="form-control" placeholder="Yazının önizleme metnini giriniz...">
      </div>
      <div class="form-group">
        <label>Yazı</label>
        <textarea v-model="post.content" cols="30" rows="5" class="form-control"></textarea>
      </div>
      <button @click="$router.push('/')" class="btn btn-danger">İptal</button>
      <button type="submit" class="btn btn-info">Kaydet</button>
    </form>
  </div>
</template>
<script>
import axios from "axios";
  export default {
    data(){
      return {
        post : {
          author : "",
          content : "",
          previewText : "",
          thumbnail : "",
          title : "",
          updatedDate : ""
        }
      }
    },
    methods : {
      onSubmit(){
        axios.post("https://vuejs-axios-2c23f-default-rtdb.firebaseio.com/posts.json",{...this.post,updatedDate= new Date()})
       then(response=>{
         console.log(reponse)
       })
       .catch(e =>console.log(e))
      }
    }
  }
</script>
