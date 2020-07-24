<template>
    <div>
        <section class="wrapper">
            <div class="flex-col">
                <img class="flex-col-2" :src="makeImagePath(product)" alt="">
                <div class="flex-col-2">
                    <h2>{{ product.name }}</h2>
                    <p>Price : ${{ product.price }}</p>
                    <p>Size : ${{ product.size }}</p>
                    <p>Color : ${{ product.color }}</p>
                    <p><em>{{ product.quantity }} left in stock</em></p>
                    <h3>Details</h3>
                    <ul>
                        <li>Material: {{product.details.material}}</li>
                        <li>Fit: {{product.details.fit}}</li>
                        <li>Maintenance: {{product.details.maintenance}}</li>
                        <li v-if="product.details.additional">Additional: {{product.details.additional}}</li>
                    </ul>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
import {imagePath} from '@/mixins/imagePath.js'

export default {
    name:'product',
    mixins:[imagePath],
    data(){
        return{
            product: this.$store.getters.product(this.$route.params.id)
        }
    },
    methods:{
        imagePath(product){
            return require(`../assets/img/products/${product.images[0]}`);
        }
    }
};
</script>

<style lang="scss">
    .flex-col{
        display: flex;
        align-items: flex-start;
    }
    .flex-col-2{
        width: 50%;
    }
</style>