<template>
    <div>
        <h1>Invoices</h1>
    </div>
</template>

<script>
import { onBeforeRouteLeave } from 'vue-router';
export default {
    setup(){
       onBeforeRouteLeave((to, from, next)=>{
           if(window.confirm('Are you sure you want to leave?')){
               next();
           }else{
               next(false);
           }
       })
    },
}
</script>