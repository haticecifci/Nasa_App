<template>
    <div class="inputWrapper">
        <input type="text" v-model="q" autofocus
        placeholder="Uzayda bir şeyler arayın."></div>

        <div class="listWrapper">
            <div v-for="item in data" :key="item">
            <ListItem :item="item"></ListItem>
            </div>
        </div>
        <div class="nodata" v-if="data.length===0 && loading===false">Üzgünüm uzayda boşluk var</div>
    
</template>
    
  <script>
import ListItem from './ListItem.vue'

    export default {
    name: 'ListWrapper',
    methods: {
        fetchData(q) {
            this.loading = true;
            fetch('https://images-api.nasa.gov/search?q=' + q).then((res) => {
                res.json().then((d) => {
                    console.log(d);
                    this.loading = false;
                    this.data = d.collection.items;
                });
            });
        }
    },
    data() {
        return {
            loading: false,
            data: [],
            q: ""
        };
    },
    watch: {
        // eslint-disable-next-line
        q(newVal, oldVal) {
            if (newVal.length > 2) {
                this.fetchData(newVal);
            }
            else {
                this.data = [];
            }
        }
    },
    components: { ListItem }
}
  </script>
   
<style scoped>

.listWrapper{
   display: grid;
   grid-template-columns: repeat(4,1fr);
   gap:20px;
}
.inputWrapper{
    width: 100%;
    display: flex;
    margin-bottom: 20px;
}

.nodata{
    text-align: center;
    width: 100%;
    color:#fff;
    font-size: 32px;
}
.inputWrapper input{
    width: 100%;
    height: 40px;
    display: flex;
    padding: 8px 16px;
    box-sizing: border-box;
    border: none;
    outline: none;
    border-radius: 16px;
    text-transform: uppercase;
}
</style>