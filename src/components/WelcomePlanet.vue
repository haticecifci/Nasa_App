<template>
  <div class="welcomeImage">
    <img :src="welcomeData.hdurl" alt="">
  </div>

  <div class="title">{{ welcomeData.title }}</div>
  <div class="text">{{ welcomeData.explanation }}</div>
</template>
  
<script>
  export default {
    name: 'WelcomePlanet',
    created(){
      fetch('https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY')
      .then((res)=>{
        res.json().then((data)=>{
            this.welcomeData={
                hdurl:data.hdurl,
                title:data.title,
                explanation:data.explanation
            }
        })
      })
    },
    data(){
        return{
            welcomeData:{
                hdurl:"",
                title:"",
                explanation:""
            }
        }
    }
    
  }
</script>
 
<style scoped>
.welcomeImage{
    width: 100vw;
    height: 100vh;
    position: relative;
}

.welcomeImage img{
    width: 100vw;
    height: 100vh;
}

.title{
    font-size: 32px;
    color:#fff;
    top:45%;
    left:25%;
    font-weight: 500;
    position: absolute;
}

.text{
    font-size: 20px;
    color:#fff;
    top:50%;
    left:25%;
    font-weight: 400;
    position: absolute;
    letter-spacing: 2px;
    max-width: 50%;
}
</style>