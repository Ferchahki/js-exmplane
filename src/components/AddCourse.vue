<template>
  <form @submit.prevent="NewCourse">
    <div class="d-grid gap-2">
    <div class="form-group d-grid gap-2">
      <label for="Title">
        Title:
        <input
          v-model="title"
          ref="title"
          id="Title"
          type="text"
          class="form-control"
        />
      </label>
    </div>
    <div class="form-group d-grid gap-2">
      <label for="Image">
        Image:
        <input
          v-model="image"
          ref="image"
          id="Image"
          type="text"
          class="form-control"
        />
      </label>
    </div>
    <div class="form-check form-check-inline">
      <label class="form-check-label">
          <input  
          v-model="typeOfpayement" 
          class="form-check-input" 
          type="radio" 
          name="typeOfpayement" 
          id="" value="Free"> Free <br>
      </label>
      <label class="form-check-label">
         <input  
            v-model="typeOfpayement"  
            class="form-check-input" 
            type="radio" 
            name="typeOfpayement" id="" value="paying" checked> Paying
      </label>
    </div>
    <div class="form-check">
      <label class="form-check-label">
        <input type="checkbox"  name="pulished" class="form-check-input"  v-model="published">
        Published
      </label>
    </div>
    <div id="my-3">
      Tags :
      <div class="form-check" v-for='tags in tags' :key="tags">
          <label class="form-check-label">
            <input type="checkbox" name="tags" class="form-check-input" :value="tags" v-model="mytags">
            {{ tags }}
          </label>
      </div>
    </div>
    <button type="submit" @click="NewCourse" class="btn btn-lg btn-primary">
      Ajouter
    </button>
    <div class="form-group">
      <label for="category">Category :</label>
      <select v-model="category" name="category" id="category" class="form-control">
         <option :key='categories.id'  v-for='categories in categories'>
          {{ categories.name }}
        </option>
      </select>
    </div>
      <!-- <div class="well">
        Titre : <p>{{ title }}</p>
        Image: <p>{{ image }}</p>
        Categorie:<p>{{ category }}</p>
        Type of payement <p>{{ typeOfpayement }}</p>
        Published <p>{{ published }}</p>
        MyTages <p>{{ mytags }}</p>
      </div> -->
    </div>
  </form>
</template>
<script>
export default {
  data() {
    return {
      title: '',
      image: '',
      categories:[
        {id:1 , name:'FullStack'},
        {id:2 , name:'Front-end'},
        {id:3 , name:'Back-end'},
        {id:4 , name:'Mobile'}
      ],
      typeOfpayement:''
      ,
      published:true,
      tags:['Framwork','Front-end','Back-end','JavaScript'],
      mytags:[],
      category: 3
    }
  },
  methods: {
    NewCourse() {
      let title = this.$refs.title.value
      let image = this.$refs.image.value
      

      if (title == ' ' || image == ' ') {
        return
      }

      const course = {
        title,
        image,
        categories,
        typeOfpayement,
        tags,
        category:this.categories.find(category=>this.categories==this.category).name 
      }

      this.$emit('add', course)

      this.$refs.title.value = ''
      this.$refs.image.value = ''
    },
  },
}
</script>
<style></style>
