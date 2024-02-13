<template>
    <div class="card">
        <img :src="item.links[0].href" >
        <div class="container">
            <h4>{{ item.data[0].title }}</h4>
            <p>{{ item.data[0].description }}</p>
            <div class="tags">
                <div class="tag-item" v-for="tag in item.data[0]?.keywords?.slice(0,3)" :key="tag">
                {{ tag }}</div>
            </div>
        </div>
    </div>
</template>


<script>
export default{
    name:"ListItem",
    props:['item']
}
</script>

<style scoped>
.tags{
    margin-bottom: 20px;
    display: none;
    gap:20px;
    flex-wrap: wrap;
    cursor: pointer;
}

.tag-item{
    padding: 8px;
    background-color: #fff;
    font-size: 12px;
    border:1px solid;
    border-radius: 16px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    color:#280d08f9;
}
.card{
    border:2px solid #fc3d21;
    box-shadow: 0 4px 8px rgba(0,0,0,0.5);
    transition: .5s;
    width: 100%;
    border-radius: 16px;
}

.card > img{
    height: 300px;
    object-fit: fill;
    border-top-left-radius:16px ;
    border-top-right-radius: 16px;
    width: 100%;
}

h4{
    color:#fc3d21;
    font-weight: 500;
}
.card:hover{
    box-shadow: 0 8px 16px rgba(0,0,0,0.8);
}

.container{
    padding: 4px 16px;
}

p{
    font-size: 14px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
}
</style>