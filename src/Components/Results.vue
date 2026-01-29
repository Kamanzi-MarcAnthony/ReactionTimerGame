<template>
    <div class="results">
        <p>Your reaction time is {{ score }} ms</p>
    </div>
    
</template>

<script>
export default {
    props: ['score']
}
</script>

<style scoped>
.results{
    font-size: 20px;
    background-color: bisque;
    width: 500px;
    height: 100px;
    margin: 20px auto;
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 15px;
}
</style>