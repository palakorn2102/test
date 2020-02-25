<template>
    <div>
        <div v-for="(item, index) in Joke" :key="index" class="contentJoke">
            <div> id : {{item.id}}</div>
            <div> joke : {{item.joke}} </div>
            <div>
                categories : 
                <div v-for="(categories, index2) in item.categories" :key="index2">
                    -{{categories}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:[
        'Joke'
    ]
}
</script>

<style>
    .contentJoke{
        border: 1px solid black;
        margin-bottom: 15px;
        padding: 10px;
        border-radius: 7px;
    }
</style>