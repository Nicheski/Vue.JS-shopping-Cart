<template>
<div class="container">
			<br />
			<h2 align="center"> Shopping Cart with Vue.Js 3</h2>
			<br />
			<form method="post">
				<div class="row">
					<div class="col-md-3" style="margin-top:12px;"  v-for="product in products" >
						<div style="border:1px solid #333; background-color:#f1f1f1; border-radius:5px; padding:16px; height:350px;" align="center">
							<img  class="img-responsive" :src="product.img" /><br />
              	
							<h4 class="text-info">{{product.name}}</h4>
						<h4 class="text-info">{{product.brand}}</h4>
           			<h4 class="text-info">${{product.price}}</h4>
							<input type="button" name="add_to_cart" @click="add(product)" style="margin-top:5px;" class="btn btn-success form-control" value="Add to Cart"  />
						</div>
					</div>
				</div>
			</form>
			<br />
			<h3 align="center">Your Cart Details</h3>
			<div class="table-responsive" id="order_table">
				<table class="table table-bordered table-striped">
					<tr  >  
						<th width="30%">Product Name</th> 
  
						<th width="20%">Price</th>  
							<th width="15%">Quantity</th>  
            		<th width="10%">Brand</th>  
						<th width="5%">Action</th>  
					</tr>

					<tr v-for = "(item,index) in items">
						<td>{{item.name}}</td>
            			<td>{{item.price}}</td>
						<td>{{item.quantity}} </td>
						<td>{{item.brand}}</td>
						<td><button type="button" name="remove_product" class="btn btn-danger btn-xs"  @click="deleteItem(index)">Remove</button></td>
            
					</tr>
					<tr>
						<td colspan="3" align="right">Total</td>
						<td colspan="2">{{setTotal}}</td>
					</tr>
				</table>
			</div>
		</div>

</template>

<script>


export default {
  name: 'App',
  components: {
  
  },

  data(){
    return {
     
      items : [],
      products : [
        {name: 'E-Sports Mouse', brand: 'Razer', quantity: 1, price: 10, img: require('/src/assets/one.jpeg') },
            {name: 'E-Sports Keyboard', brand: 'Cherry', quantity: 1, price: 20, img: require('/src/assets/two.jpeg')},
                {name: 'E-Sports Mouse', brand: 'Razer', quantity: 1, price: 30, img: require('/src/assets/three.jpeg') },
                    {name: 'E-Sports Keyboar', brand: 'Razer', quantity: 1, price: 40, img: require('/src/assets/four.jpeg') },
                        {name: 'E-Sports Headset', brand: 'Hyperx', quantity: 1, price: 50, img: require('/src/assets/five.jpeg') },
                            {name: 'E-Sports  Mouse Pad', brand: 'Razer', quantity: 1, price: 60, img: require('/src/assets/six.jpeg') },
                                {name: 'E-Sports Mouse', brand: 'Razer', quantity: 1, price: 70, img: require('/src/assets/seven.jpeg') },
                                    {name: 'E-Sports monitor', brand: 'Benq', quantity: 1, price: 80, img: require('/src/assets/eight.jpeg') },
                                       
      ]
    }
  },
  methods:{
  add(products) {
        
  
          
          this.items.push(products);

     
        
       
      },
deleteItem(index){ 
            this.items.splice(index, 1)
}
      
  },

  computed: {
    setTotal(){
     let total = 0;
     this.items.forEach(item => {
       total = total + (item.price * item.quantity);
     });
     return total;
     
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.popover
		{
		    width: 100%;
		    max-width: 800px;
		}


</style>
