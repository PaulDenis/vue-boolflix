<template>
    <div>

    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Main',
    created: function() {
        axios
            .get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: '566ba9ef10ccfee32a5a7380346f0a0a',
                    query: 'ritorno',
                    language: 'it-IT'
                }
            })
            .then(
                (res) => {
                    console.log(res);
                }
            )
    },
    props: {
        searching: String
    },
    data() {
        return {
        }
    }
}
</script>

<style lang="scss" scoped>
    div {
        height: calc(100vh - 100px);
        background-color: #E94F02;
    }

</style>