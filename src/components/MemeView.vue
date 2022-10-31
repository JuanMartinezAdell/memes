<template>
    <!-- div class="col-3 border border border-light meme">
        <p>{{ meme.name }}</p>
        <img :src="meme.url" :alt="meme.name" class="fluid" />
    </div -->
    <div class="col-3 border border border-0 meme">
        <div class="card" style="max-width">
            <img :src="meme.url" class="card-img-top p-2" :alt="meme.name">
                <div class="card-body" aria-hidden="true">
                <p class="card-text nb-2">{{ meme.name }}</p>
            </div>
        </div>
    </div>
    <!--div class="col-3 border border border-ligth meme">
        <div class="card text-bg-dark">
            <img :src="meme.url" class="card-img-top" :alt="meme.name">
                <div class="card-img-overlay">
                    <h5 class="card-title">{{ meme.name }}</h5>
                </div>
        </div>
    </div -->
</template>

<script>
export default {
    props: {
        meme: Object,
    }

}
</script>

<style scoped>
    .meme {
        height: 350px;
        display: flex;
        flex-direction: column;
        align-items: center;
        border: 1px solid grey;
    }

    .meme img {
        max-height: 250px;
        max-width:  300px;
    }
</style>