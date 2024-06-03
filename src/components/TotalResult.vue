<script>
import { store } from "../store";

export default {
    data() {
        return{
            store
        }
    },
}
</script>

<template>
    <div class="text-center mb-5 fw-bold">Found {{this.store.characterArray.length}} characters</div>
</template>