<template>
<div>
    <div class="container m-auto grid lg:grid-cols-3 gap-5 items-center py-5">
            <div class="col-span-1">
                <img :src="meal.meals[0].strMealThumb" alt="" width="400" height="400" class="rounded-full">
            </div>
            <!-- meal.meals -->

            <div class="col-span-2">
                <h1 class="text-2x1 font-bold">{{ meal.meals[0].strMeal }}</h1>
                    <p>{{ meal.meals[0].StrInstructions }}</p>
                    <h1 class="text-xl text-red-500">Video Tutorial</h1>
                    <a :href="meal.meals[0].strYoutube" target="_blank">How to Make {{ meal.meals[0].strMeal }}</a>
            </div>
    </div>
</div>
</template>

<script setup>
const route = useRoute();
const {
    data: meal
} = await useFetch(`https://www.themealdb.com/api/json/v1/1/lookup.php?i=${route.params.id}`)
</script>

<style lang="scss" scoped>

</style>
