<template>
    <div>
       list View
       <ul>
           <list-item  v-for="item in items" :key="item.id" :item="item" />
       </ul>
    </div>
</template>


<script>
import listItem from './listItem';
export default {
    components:{
        listItem
    },
    data(){
        return{
            items:[]
        }
    },
    methods:{
        getList(){
            axios.get('api/items')
            .then(response => {
                this.items = response.data
            })
            .catch(error => {
                console.error(error);
            })
        }
    },
    mounted() {
        this.getList();
    }

}
</script>

<style scoped>
    .item{
        background: #e6e6e6;
        padding: 5px;
        margin-top: 5px;
    }
</style>