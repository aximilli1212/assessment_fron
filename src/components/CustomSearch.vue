<template>
    <v-row justify="center">
        <v-col cols="12" sm="6" md="4" lg="7">
            <v-autocomplete
                    @keypress.enter.prevent="searchForm"
                    @select="selected"
                    class="elevation-0"
                    v-model="model"
                    :items="items"
                    :loading="isLoading"
                    :search-input.sync="search"
                    clearable
                    hide-details
                    hide-selected
                    item-text="name"
                    item-value="id"
                    solo
                    placeholder="Find books by title, Isbn and Year ....
"
                    outlined
                    rounded
                    dense
            >
                <template v-slot:no-data>
                    <v-list-item>
                        <v-list-item-title>
                            Find books by title, Isbn and Year ....
                        </v-list-item-title>
                    </v-list-item>
                </template>
                <template v-slot:item="{ item }">
                    <v-list-item-avatar
                            color="white"
                            class="headline font-weight-light white--text"
                    >
                        <v-img
                                :src="`${imgHost}imgs/products/${item.product_type.slug}/${item.img_url}?w=60`"
                                :lazy-src="`${imgHost}imgs/products/${item.product_type.slug}/${item.img_url}?w=8`"
                        ></v-img>
                    </v-list-item-avatar>
                    <v-list-item-content>
                        <v-list-item-title class="font-weight-bold" v-text="item.name"></v-list-item-title>
                        <v-list-item-subtitle>{{item.product_type.name}}@<i class="caption red--text">{{item.company.name}}</i></v-list-item-subtitle>
                    </v-list-item-content>
                    <v-list-item-action>
                        <i class="green--text text--darken-2">{{item.price | currency}}</i>
                    </v-list-item-action>
                </template>
            </v-autocomplete>
        </v-col>
    </v-row>
</template>

<script>
    export default {
        data: () => ({
            isLoading: false,
            items: [],
            model: null,
            search: null,
            tab: null,
        }),

        watch: {
            model (val) {
                let selectProduct = this.items.filter(e=>{
                    return e.id === val;
                })
                console.log({selected:selectProduct});
            },
            select(val){

            },
            search (val){

                let self = this;
                // Items have already been loaded
                if (this.items.length > 0) return
                this.isLoading = true;
                // Lazily load input items
                axios.post(`${process.env.VUE_APP_HOST_URL}/search_books` , val)
                    .then(response => {
                        self.items = response.data;
                    })
                    .catch(error => {
                        console.log(error)
                    })
            },
        },
        methods:{
            searchForm(){
                this.$router.push({name: 'products-search', params: {search: this.search}})
            },

            selected(){
                // alert("pooped");
            },
        }
    }
</script>

<style scoped>

</style>
