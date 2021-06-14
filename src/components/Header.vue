<template>
    <div>
        <img src="../assets/images/foxlix.png" alt="Logo" class="logo">
        <div>
            <input v-model="query" type="text" placeholder="Cerca..." 
            @keyup.enter="$emit('cerca', query)" />
            <button type="button" @click="$emit('cerca', query)">Cerca</button>
        

        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    data: function () {
        return {
            query: "",
            reset:""
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
        .logo {
            height: 50px;
            margin-left: 20px;
        };
        input {
            margin-right: 20px;
        }
        button {
            margin: 5px;
            padding: 0px 5px;
        }
    }
    
</style>