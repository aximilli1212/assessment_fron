<template>
    <section>
        <v-row  justify="center">
            <v-col xs="8" class="my-4">
                <v-row justify="center" v-if="loadingTrending">
                    <v-progress-circular indeterminate size="72" color="primary"></v-progress-circular>
                </v-row>
                <v-row justify="center" class="my-n12" v-else>
                    <v-col v-for="(book, i) in bookList" :key="i" xs="6" sm="3" class="mx-0">
                        <book-card :book_details="book"> </book-card>
                    </v-col>
                </v-row>
            </v-col>
        </v-row>
    </section>
</template>

<script>
    import axios from 'axios'
    import BookCard from "../components/BookCard.vue";

    export default {
        data () {
            return {
                loadingTrending: false,
                bookList: [],
                loading: false
            }
        },
        mounted () {
            axios
                .get('http://doc2.vag/api/books')
                .then(response => {
                    console.log({books: response.data.data});
                    this.bookList = response.data.data;
                    this.loading = false
                })
                .catch(error => {
                    console.log(error)
                })
        },
        components:{
            BookCard,
        }
    }
</script>
<style lang="scss" scoped>

</style>
