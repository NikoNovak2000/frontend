<template>
  <html lang="en">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>BrziChesse</title>

    
    <link rel="stylesheet" href="/index.css">

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">


</head>
<body>
  <div id="container" class="container">


      <div id="foodItems">
        <!-- 1. -->
        <div id="burger" class="burger">
          <p id="foodCategory">Burger</p>

        </div>

        <!-- 2. -->
        <div id="kebab" class="kebab">
          <p id="foodCategory">Kebab</p>
       </div>

       <!-- 3. -->
       <div id="pizza" class="pizza">
        <p id="foodCategory">Pizza</p>
       </div>

        <!-- 4. -->
        <div id="seafood" class="seafood">
          <p id="foodCategory">Seafood</p>
        </div>

       <!-- 5. -->
        <div id="sides" class="sides">
          <p id="foodCategory">Sides</p>
        </div>
      </div>

        
      <h1> {{items[1]}} </h1>

    </div>

</body>
</html>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'


export default{
  el: '#app',
  data() {
    return {
      items: []
    }
    },
  components: {
    HelloWorld
  },
 
  mounted(){
     axios.get('http://127.0.0.1:5000/items')
      .then((response) => {
         console.log('Ovo su podaci koji se dohvacaju' + response.data.data)
         this.items = response.data
      })
      
    }
}

function displayItems(){
    var burger = document.getElementById('burger')

    const burgerData = {items}.filter(item => item.category=='burger');
    console.log(burgerData);

     burgerData.map(item=> {
        var itemCard = document.createElement('div');
        itemCard.setAttribute('id','itemCard');

        var cardTop = document.createElement('div');
        cardTop.setAttribute('id','cardTop');

        var img = document.createElement('img');
        img.src = item.img;

        var itemName = document.createElement('p');
        itemName.setAttribute = ('id', 'itemName');
        itemName.innerText = item.name;

        var itemPrice = document.createElement('p');
        itemPrice.setAttribute('id','itemPrice');
        itemPrice.innerText = 'Price: ' + item.price + ' €';

        itemCard.appendChild(cardTop);
        itemCard.appendChild(img);
        itemCard.appendChild(itemName);
        itemCard.appendChild(itemPrice);

        burger.appendChild(itemCard);
    })
  }
//displayItems();





</script>

<style scoped lang="scss">

*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

html{
    height: 100%;
}

body{
    height: 100%;
}

.container{
    display: grid;
    grid-template-columns: 250px 1fr 350px;
    height: 100%;
    overflow: hidden;
}

.slikaLogo img{
    width: 190px;
    height: 180px;
    padding-left: 20px;
    padding-top: 20px;
    margin-top: 35px;
}

.menuItem a{
    display: block;
    text-decoration: none;
    color: #070303;
    font-size: 20px;
    padding: 0px 14px;
    margin: 10px;
}

.menuItem a:hover{
    background: #ffd3d3;
}

#menu{
    background: #f34d2c;
}

.foodItems{
   display: none;
}

#foodContainer{
    background: #3ba552;
    box-sizing: content-box;
    overflow: scroll;
    overflow-x: hidden;
}

#header{
    background: #a3ffa8;
    padding-top: 50px;
    padding-bottom: 15px;
    display: flex;
    align-items: center;
    position: sticky;
    justify-content: space-between;
    z-index: 1;
}

.yourAddress {
    border:#070303 2px solid;
    color: #070303;
    padding: 4px 8px;
    border-radius: 4px;
    width: 250px;
    overflow: hidden;
    text-overflow: ellipsis;
    text-transform: capitalize;
    cursor: pointer;
    margin-left: 10px;
    background: #ffffff;
}
 
.addBox i{
    font-size: 16px;
}

.util i{
    border:#006ba8 2px solid;
    color: #006ba8;
    font-size: 16px;
    margin: 0 14px;
    padding: 8px 16px;
    cursor: pointer;
    border-radius: 16px;
    background: #ffffff;
}

.util i:active, .user i:active{
    color:#ffffff;
    background: #1797ff;
}

#hamburger,#cheeseburger,#baconburger,#chickenburger,#doubleburger{
    margin-top: 40px;
}



#foodCategory, .menuItem{
    margin: 14px;
    font-size: 36px;
    color: #ff520e;
}

#itemCard{
    width: 240px;
    height: 220px;
    background: #b9bcdf;
    padding: 8px;
    margin: 8px;
    transition: 05s all ease-in-out;
    display: inline-block;
    border-radius: 5px;
    cursor: pointer;
}

#itemCard img{
    width: 160px;
    height: 100px;
    display: block;
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-radius: 50%;
    margin: auto;
    transition: 0.5s all ease-in-out;
}

#itemCard img:hover{
    transform: scale(1.2);
}

#itemName{
    margin: 6px 0;
    font-weight: 600;
    color: #000000;
    font-size: 20px;
}

#itemPrice{
    margin: 0px;
    font-weight: 550;
    color: #000000;
    font-size: 16px;
}

#cardTop {
    display: flex;
    margin: 8px 0;
    justify-content: space-between;
}

#rating{
    color: #fafa18;
    padding: 5px;
    background: #070303;
    font-size: 12px;
    border-radius: 12px;
}

.fa-heart-o{
    padding: 6px;
    background: #ffffff;
    cursor: pointer;
    border-radius: 50%;
}

.toggle-heart{
    background: #ff0000;
    color: #ffffff;
}

::-webkit-scrollbar{
    display: none;
}

#cart{
    background: #f34d2c;
    padding-right: 30px;
    overflow-y: scroll;
}

.fa-user-circle{
    border:#006ba8 2px solid;
    color: #006ba8;
    font-size: 16px;
    margin: 0 14px;
    padding: 8px 18px;
    cursor: pointer;
    border-radius: 16px;
    background: #ffffff;
    margin-top: 50px;
    margin-bottom: 10px;
}

.taste-header{
    padding-top: 40px;
    padding-bottom: 10px;
    position: sticky;
    top: 0;
    background: #ffffff;
}

.itemMenu{
    margin: 0;
    font-size: 30px;
    margin-top: 40px;
    color: #d4d4d4;
}

.border{
    width: 160px;
    height: 4px;
    margin: 3px 0;
    margin-bottom: 30px;
    border-radius: 2px;
    background-color: #181414;
}

.listCard{
    display: flex;
    align-items: center;
    margin-top: 15px;
    border-radius: 25px;
    cursor: pointer;
    transition: 0.1s all ease-in-out;
}

.listCard img{
    width: 80px;
    height: 50px;
    border-radius: 50%;
}

.listCard:hover{
    background: white;
}

.listCard:hover img{
    transition: 0.3s ease-in-out;
    transform: scale(1.2);
}

.listName{
    font-size: 18px;
    margin: 0 10px;
    text-decoration: none;
    text-transform: capitalize;
    color: #070303;
}

#cartPage {
     background: rgb(255, 255, 255);
     margin: 40px 10px;
     margin-right: 50px;
     padding: 20px 30px;
     padding-bottom: 30px;
     position: relative;
}

#cartTitle{
    font-size: 35px;
    color: red;
}

#cartPage table{
    width: 100%;
    margin-top: 20px;
    text-align: center;
}

#cartPage table head td{
    font-size: 20px;
    padding-bottom: 10px;
}

#mTotalAmount{
    display: none;
}

#cartPage table tbody td{
    padding: 10px 0;
    font-size: 20px;
}

#cartPage table tbody button{
    outline: none;
    border: none;
    font-size: 16px;
    background: none;
    background: lightcoral;
    color: white;
    border-radius: 3px;
    cursor: pointer;
    margin: 0 5px;
    padding: 3px 8px; 
}

#cartPage table tbody img{
    width: 80px;
    height: 80px;
    border-radius: 50px;
}

.cartToggle{
    display: none;
}

#checkout{
    text-align: center;
    margin: 40px auto;
    border-radius: 5px;
    background: white;
    padding: 10px 20px;
}

#checkout p{
    margin: 15px 0;
    float: left;
}

#totalPrice,#totalItem{
    font-size: 20px;
    color: red;
}

.checkoutBtn{
    outline: none;
    border: none;
    background: #26a2eb;
    padding: 10px 25px;
    border-radius: 20px;
    font-size: 16px;
    bottom: 30px;
    margin: 15px 0;
    cursor: pointer;
}

.checkoutBtn:active{
    color:#52d9e2;
    background: none;
    border: 1px solid #52d9e2;
}

#delievery{
    font-size: 16px;
    color: #00ac00;
}
</style>