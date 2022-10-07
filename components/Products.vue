<script setup>
const props = defineProps({
  title: {
    type: String,
  }
})
const { data: products } = await useFetch(()=>`https://dummyjson.com/products/`)

</script>

<template>
        <!-- Products Start -->
        <div class="container-fluid pt-5 pb-3">
        <h2 class="section-title position-relative text-uppercase mx-xl-5 mb-4">
            <span class="bg-secondary pr-3">
                {{title}}
            </span>
        </h2>
        <div class="row px-xl-5">

            <div class="col-lg-3 col-md-4 col-sm-6 pb-1"
                 v-for="product in products.products" :key="product.id"
            >
                <div class="product-item bg-light mb-4">
                    <div class="product-img position-relative overflow-hidden">
                        <img class="img-fluid w-100" :src="product.thumbnail" alt="">
                        <!-- <div class="product-action">
                            <a class="btn btn-outline-dark btn-square" href=""><i class="fa fa-shopping-cart"></i></a>
                            <a class="btn btn-outline-dark btn-square" href=""><i class="far fa-heart"></i></a>
                            <a class="btn btn-outline-dark btn-square" href=""><i class="fa fa-sync-alt"></i></a>
                            <a class="btn btn-outline-dark btn-square" href=""><i class="fa fa-search"></i></a>
                        </div> -->
                    </div>
                    <div class="text-center py-2">
                        <a class="h6 text-decoration-none text-truncate" href="">
                            {{product.title}}
                        </a>
                        <div class="d-flex align-items-center justify-content-center mt-2">
                            <h5>
                                {{product.price - (product.discountPercentage/100)*product.price }}
                            </h5>
                            <h6 class="text-muted ml-2"><del>{{product.price}}</del></h6>
                        </div>

                        <!-- <div class="d-flex align-items-center justify-content-center mb-1">
                            <small class="fa fa-star text-primary mr-1"></small>
                            <small class="fa fa-star text-primary mr-1"></small>
                            <small class="fa fa-star text-primary mr-1"></small>
                            <small class="fa fa-star text-primary mr-1"></small>
                            <small class="fa fa-star text-primary mr-1"></small>
                            <small>(99)</small>
                        </div> -->
                    </div>
                </div>
            </div>
           

        </div>
    </div>
    <!-- Products End -->
</template>

<style>
.product-item{
    box-shadow: 1px 1px 10px grey;
}
.product-img{
    height: 200px;
}
.product-img img{
    width: 100%;
    height: 100%;
    object-fit: cover;
}
</style>