<template>
    <h1 class="text-primary">{{ title }}</h1>
    <div class="total-show">
        <select @change="changeTotalShow" class="form-select m-2" aria-label="Todos">
            <option value="">Todos</option>
            <option value="5">5</option>
            <option value="10">10</option>
            <option value="20">20</option>
        </select>
    </div>
    <div class="row">
        <template v-for="meme in memes" :key="meme.id">
           <Meme :meme="meme" />
        </template>
    </div>
</template>

<script>
import { onMounted, computed  } from  "vue";
import { useStore } from "vuex";
import Meme from "./MemeView";

export default {
    components: {
        Meme,

    },
    setup() {
        const store = useStore();
        const memes = computed(() => store.state.memes);

        onMounted(() => {
            store.dispatch("getMemes");
        });

        const changeTotalShow = (e) => {
            store.dispatch("getMemes", {
                total: e.target.value,
            });
        };

        return {
            title: store.state.titleApp,
            memes,
            changeTotalShow,
        };
    },
};
</script>

<style scoped>
    h1 {
        text-align: center;
    }
    .total-show {
        display: flex;
        justify-content: flex-end;
        margin-bottom: 5px;
    }
</style>