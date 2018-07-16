<template>
    <div class="col-sn-6 col-md-4">
        <div class="panel panel-danger">
            <div class="panel-heading">
                <h3 class="panel-title">{{ stock.name }}
                    <small>(Price: {{stock.price}}) | Quantity: {{stock.quantity}}</small>
                </h3>
            </div>
            <div class="panel-body">
                <div class="pull-left">
                    <input type="number" class="form-control" placeholder="Quantity" v-model.number="quantity" :class="{danger: insufficientQuantity}">
                </div>
                <div class="pull-right">
                    <button class="btn btn-danger" 
                    @click="sellstock"
                    :disabled="insufficientQuantity || quantity <= 0||!Number.isInteger(quantity)"> {{insufficientQuantity ? 'Insuffcient Quantity' : 'Sell'}} </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { mapActions } from 'vuex';

export default {
    props:['stock'],
    data(){
        return {
            quantity: 0
        }
    },
    computed:{
        insufficientQuantity(){
            return this.quantity > this.stock.quantity;
        }
    },
    methods:{
        ...mapActions([
            'sellStock'
        ]),
        sellstock(){
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            };
            this.sellStock(order);
            this.quantity = 0 ;
        }
    }
}
</script>
<style scoped>
    .danger{
        border: 1px solid red;
    }
</style>