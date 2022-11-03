<template>
  <div class="hello">
    
    <div className = 'cartProba'>
     <form @submit="onSubmit">
     <div class="cartProba"> <input v-model="formdata.name" placeholder="Unesi ime" /></div>
     <div class="cartProba">  <input v-model="formdata.quantity" placeholder="Unesi kolicinu" /></div>
     <div class="cartProba"> <input v-model="formdata.img" placeholder="Unesi url slike" /></div>
     <div class="cartProba"> <input v-model="formdata.price" placeholder="Unesi cijenu" /></div>
     <button type="submit">Submit</button>
     </form>
  </div>
  </div>
</template>



<script>
import { VueElement } from '@vue/runtime-dom'
import axios from 'axios'

export default {
  name: 'cart',
  data () {
    return {
       formdata:{ name:'',  quantity: '', img: '', price: '' }
       // this is formdata object to store form values
    }
  },
  methods: 
  {

    dodajItem(payload){
      axios.post('http://127.0.0.1:5000/app/cart/dodaj', payload)
      .then(res => {
         console.log('ovo su podaci koji se spremaju u bazu' + payload)
      })
      .catch(err => { 
         console.log({data : this.formdata})
         
      })
    },
    onSubmit(){
      const payload = {
        name: this.formdata.name,
        quantity: this.formdata.quantity,
        img: this.formdata.img,
        price: this.formdata.price,
      };
      this.dodajItem(payload)
  }
  }
  ,
  mounted () {

  },
  components: {

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.cartProba {
    display:block; 
    width:100%; 
    padding-bottom: 10px;
}

</style>
