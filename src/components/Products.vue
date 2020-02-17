<template>
    <div class="">
         <ul>
            <ProductsItem
                v-for="proditem of prod"
                :key="proditem.id"
                v-bind:proditem="proditem"
            />
         </ul>
    </div>
</template>

<script>
import ProductsItem from '@/components/ProductsItem'
export default {
    props: ['prod'],
    components:{
        ProductsItem
    }
}
</script>