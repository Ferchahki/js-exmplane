<template>
  <HeaderTemp />
  <div class="container">
    <div class="row">
      <div class="col-md-6 mx-auto">
        
       <h3 class="text-center">{{ message }}</h3>
      </div>
    </div>
    <CourseTem>
      <ol class="breadcrumb">
          <li class="breadcrumb-item"><a href="#">Home</a></li>
          <li class="breadcrumb-item active" aria-current="page">list of courses</li>
      </ol>
      <template  v-slot:button-right>
          <!-- <button   class="btn btn-sm btn-success">Add</button> -->
      </template>
    </CourseTem>

  </div>

  <FooterTemp 
          url="http://abdessamad-elferchakhi.com/" 
          titre="Author" 
          text="GET UR CERTIFCATE"
    />
 
</template>

<script>
import HeaderTemp from './components/HeaderTemp';
import CourseTem from './components/CourseTem';
import FooterTemp from './components/FooterTemp';
export default {
  name: 'App',
  components:{
    HeaderTemp,
    CourseTem,
    FooterTemp
  },
  data(){
    return {
      message:"Courses on this platforme"
    }
   
  },
  methods: {
    handlcilck(){
      console.log(this.$refs.book.value);
      this.$refs.book.ClassList.add('active');
      this.$refs.book.focus();
    },

    displyForm(){
        this.ShowForm=!this.ShowForm;
    }

   
    
  }
}
</script>

<style>

</style>
