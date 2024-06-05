<script>
import { store } from "../store";

export default {
    data() {
        return {
            store,
            selectedStatus: ["All", "Alive", "Dead", "Unknown"],
            inputText: ""
        }
    },
}
</script>

<template>
    <form class="container d-flex w-50">
        <input v-model="inputText" class="form-control mb-5 mx-4 w-50" type="search" placeholder="Search character" aria-label="Search"   >
        <select class="form-select w-50 mx-auto mb-5" aria-label="Default select example" @change="$emit('statusChanged')" v-model="this.store.selectedStatus">
            <option :value="status" v-for="status in selectedStatus">{{status}}</option>
        </select>
        <button @click="$emit('searchEvent', inputText)" type="submit" class="mb-5 mx-4 btn btn-primary">Search</button>
        <button @click="$emit('resetEvent'); inputText= ''" type="button" class="mb-5 btn btn-warning">Reset</button>
    </form>
</template>