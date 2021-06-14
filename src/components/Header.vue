<template>
    <div>
        <img src="../assets/images/foxlix.png" alt="Logo" id="logo">
        <div>
            <input v-model="query" type="text" placeholder="Cerca..." 
            @keyup.enter="$emit('cerca', query)" />
            <!-- <button type="button" @click="$emit('search', query)">Cerca</button> -->
        

        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    data: function () {
        return {
            query: ""
        }
    }
}
</script>

<style lang="scss" scoped>

    div {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #FF8303;
        height: 100px;
        #logo {
            height: 50px;
            margin-left: 20px;
        };
        input {
            margin-right: 20px;
        }
    }
    
</style>