<template lang="">
    <div class="row" v-if="ShowForm">
        <div class="col-md-6 mx-auto">
            <AddCourse  @add="addcourse($event)"/>
        </div>
    </div>


    <div class="row">
        <div class="col-md-6">
            <nav aria-label="breadcrumb">
                <slot>no content</slot>
            </nav>
        </div>
        <div class="col-md-6 text-right">
            <slot name="button-right"></slot>
            <button  @click="displayForm" 
                    class="btn btn-sm" 
                    :class="{'btn-success':!ShowForm ,'btn-dark':ShowForm }"
            >{{ ShowForm ? 'CLOSE' : 'NEW' }}</button>
        </div>
       
    </div>
    <div class="row">
        <div class="card  col-md-4" 
                v-for="courses in courses"
                :key="courses.id">
            <OneCourse  
                    :courses="courses"
                    @delete="deleteOneCourse($event)"
            />
        </div>
    </div>
    <teleport to="#alert" v-if="courseDeleted">
        <div class="alert alert-danger text-center">
             <strong>Course is deleted ! </strong>
        </div>
    </teleport>
    <teleport to="#alert" v-if="courseAdd">
        <div class="alert alert-success text-center">
             <strong>Course is Add ! </strong>
        </div>
    </teleport>
</template>
<script>
import OneCourse from './OneCourse';
import AddCourse from './AddCourse';
export default {
    components:{
        OneCourse,
        AddCourse
             },
    data(){
        return {
            courseAdd:false,
            courseDeleted:false,
            ShowForm:false,
            courses:[
                {
                id:1,
                titre:"LEARN DOCKER",
                image:"https://img-c.udemycdn.com/course/480x270/3490000_d298_2.jpg",
                category:'Framwork',
                tags:['framwork','cloud'],
                },
                {
                id:2,
                titre:"LEARN REACT JS",
                image:"https://img-c.udemycdn.com/course/240x135/2365628_0b60_9.jpg",
                category:'Front-end',
                tags:['js','code'],
                },
                {
                id:3,
                titre:"LEARN LARAVL Advanced",
                image:"https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://cdn.filestackcontent.com/TJsOPOnzRqOUQNT2gn1w",
                category:'back end',
                tags:['php'],
                },
            ]
        }
   
    },
    methods:{

        
        deleteOneCourse(id){
            this.courses=this.courses.filter (courses => courses.id != id);
            this.courseDeleted=true;
            setTimeout(() => {
                this.courseDeleted=false
                
            }, 3000);
        },

        addcourse(course){
            // add last
            //this.courses.push(course);
            // add first
            // this.courses.unshift(course);
            this.courses=[course, ...this.courses];
            this.ShowForm=false;
            this.courseAdd=true;
            setTimeout(() => {
                this.courseAdd=false
            }, 2000);
    
        },
        displayForm(){
            // desactiver form flase and true
            this.ShowForm =!this.ShowForm;

        }
    }
        
    
}
</script>
<style scoped>
    h3{
        color:red;
    }
</style>



   