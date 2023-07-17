<template>
   
<div>

    <!-- product card section -->
    <section v-if="pending" >
        <img src="~/assets/images/loading.gif" alt="">
    </section>
    <section v-else>
        <div class="mb-3">
            <label for="" class="from-lable">Select</label>
            <select class="form-select" aria-label="Default select example" v-model="name" @change="getUrl(name)">
                <option selected> menu</option>
                <option :value="category.strCategory" v-for="(category, index) in categoryData.categories" :key="index">{{ category.strCategory }}</option>
            </select>
        </div>
        <div class="conatiner ms-auto grid grid-cols-4 gap-3 py-3 px-2">
            <div v-for="(p,index) in data.meals" :key="index">
                <nuxt-link :to="`products/${p.idMeal}`">
                    <product-card :product="p" />
                </nuxt-link>
            </div>
        </div>
    </section>

    <!-- form section -->
    <section class="py-5 m-4">
        <form-component></form-component>
    </section>
</div>
</template>

<script setup>
let name ="";
const url = ref(`https://www.themealdb.com/api/json/v1/1/filter.php?c=Seafood`)
const {data: categoryData} = await useFetch("https://www.themealdb.com/api/json/v1/1/categories.php")
const {
    data,pending
} = useFetch(url, {
    refetch: true
});

function getUrl(category) {
    url.value = (`https://www.themealdb.com/api/json/v1/1/filter.php?c=${category}`)
}
</script>

<style lang="scss" scoped>

</style>
