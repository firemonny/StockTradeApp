<template>
    <div>
        <h1>Trade or view your profolio</h1>
        <h4>You may Save & Load your data</h4>
        <h6>Click End Day to begin a new day</h6>
        <hr>
        <p>Your funds is {{funds}}</p>
    </div>
</template>
<script>
import {mapGetters} from 'vuex';
export default {
    computed:{
        ...mapGetters({
            'portforliofund': 'funds'
        }),
        funds(){
            return this.portforliofund;
        }
    }
}
</script>
