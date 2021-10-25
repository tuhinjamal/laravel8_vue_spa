<template>
    
    <div class="addItem">

        <input type="text" v-model="item.name" />
        <button class="button button2" 
        @click="addItem()"
        >Blue</button>
       
    </div>

</template>


<script>
export default {
    data: function () {
        return{
            item:{
                name:""
            }
        }
    },
    methods:{
        addItem(){
            if (this.item.name == "") {
                return;
            }
            axios.post('api/item/store',{
                item: this.item
            })
            .then(response =>{
                if (response.status == 201) {
                    this.item.name == "";
                }
            })
            .catch(error =>{
                console.error(error);
            })
        }
    }
}
</script>

<style scoped>
    .button {
  background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 12px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
}
.button2 {
  background-color: white; 
  color: black; 
  border: 2px solid #008CBA;
  border-radius: 8px;
}

.button2:hover {
  background-color: #008CBA;
  color: white;
}
</style>