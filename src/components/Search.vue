<template>
  <div class="hello">
    <form @submit.prevent="handleSubmit">
        <label>{{label}}</label>
        <input type="text" v-model="state.name"/>
        <input type="submit" value="search">
    </form>
  </div>
</template>

<script lang="ts">
import { reactive } from '@vue/composition-api'

export default {
    name:"Search",
    props:{
        label: String
    },
    setup(label:string,{emit}: any) {
        const state = reactive({
            name: ""
        })
    
        return {
            handleSubmit(event:any) {
                emit("search-me", state.name);
            },
            state
        }
    },
}
</script>
