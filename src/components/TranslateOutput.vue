<template>
 <div class="head">
    <h2>{{translatedText}}</h2>
 </div>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['translatedText']
 
}
</script>
<style>
    .head{
        font-family: Arial, Helvetica, sans-serif;
        font-weight: bold;
        font-size: 24px;
        display: flex;
        justify-content: center;
        color: #085972b9;
    }
</style>
