<script>
export default {
    props:{
        charObj: Object
    },
}
</script>

<template>
    <div class="card mb-4 bg-transparent" style="width: 18rem;">
        <img :src="charObj.image" class="card-img-top shadow" :alt="charObj.name">
        <div class="card-body">
            <h5 class="card-title">{{charObj.name}}</h5>
            <p class="card-text">{{charObj.status}}<br>{{charObj.species}}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    border: none;

    .card-img-top{
        border-radius: 50%;
    }
}
</style>