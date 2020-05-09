<template>
    <div class="col-12">
        <v-card
                style="border-radius:15px"
                class="book_card mx-auto my-4"
                to=""
        >
            <v-img
                    lazy-src="https://cdn.vuetifyjs.com/images/cards/store.jpg"
                    src="https://cdn.vuetifyjs.com/images/cards/store.jpg"
                    height="200"
            >
                <template v-slot:placeholder>
                    <v-row
                            class="fill-height ma-0"
                            align="center"
                            justify="center"
                    >
                        <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                    </v-row>
                </template>
            </v-img>
            <v-card-title class="my-n4 text-center d-block">
                {{prodSet.title}}<br />
                <i class="caption">{{prodSet.title}}</i>
                <div class=" subtitle-2 black--text">
                   pipe
                </div>
            </v-card-title>

            <v-card-actions class="text-center d-block mt-n2">
                <v-btn
                        color="blue darken-1"
                        outlined
                        rounded
                >

                    Add to cart
                    <v-icon right>mdi-cart</v-icon>
                </v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
    export default {
        name: "book_card",
        props:[
            'book_details'
        ],
        data: () => ({
            loading: false,
            selection: 1,
        }),
        computed:{
            prodSet(){
                return this.book_details;
            },
        },
    }
</script>

<style scoped>
    .book_card{
        border:1px solid #e3e3e3;
        border-radius:10px 10px 10px 20px;
    }

</style>
