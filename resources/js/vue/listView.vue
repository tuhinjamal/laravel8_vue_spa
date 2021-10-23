<template>
    
    <div>
       list View
       <div v-for="[item,index] in items " :key="index">
           <list-item
                :item="item"
                class="item"
           />
       </div>
       
    </div>

</template>


<script>
import listItem from './listItem';
export default {
    props:['item'],
    components:{
        listItem
    },
    data: function(){
        return{
            items:[]
        }
    },
    methods:{
        getList(){
            axios.get('api/items')
            .then(response => {
                this.item = response.data
                //console.log(response);
            })
            .catch(error => {
                console.error(error);
            })
        }
    },
    created() {
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