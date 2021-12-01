<template>
    <main>
        <v-item-group active-class="primary">
        <v-container fluid>
                <div>
                    <v-row>
                        <v-col cols="12" md="4">
                            <div class="d-flex items-center">
                                <v-text-field
                                    v-model="search"
                                    placeholder="Password"
                                    append-icon="mdi-magnify"
                                    dense
                                    outlined
                                    block
                                    height="40"
                                    :required="true"
                                    class="ma-0 p-0 mb-3"
                                />
                                <v-btn
                                    class="ml-1"
                                    depressed
                                    height="40"
                                    width="40"
                                    :loading="loading"
                                    :disabled="loading"
                                    color="primary"
                                    @click="loader = 'loading'"
                                    >
                                    <v-icon>
                                        mdi-filter
                                    </v-icon>
                                </v-btn>
                            </div>
                        </v-col>
                        <div>
                        </div>
                    </v-row>
                </div>

                <v-row>
                    <v-col  cols="12" >
                        <div class="text-subtitle-1 text-left font-weight-normal grey--text mb-2" v-if="!bookRequests">
                            No book request yet, please check back !
                        </div>
                        <template>
                            <v-simple-table>
                                <template v-slot:default>
                                <thead>
                                    <tr>
                                    <th class="text-left">
                                        <div class="text-subtitle-1 text-left font-weight-medium grey--text mb-2">Book <span class="primary--text">Title</span></div>
                                    </th>
                                    <th class="text-center">
                                        Number of requests
                                    </th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr
                                        v-for="item in bookRequests"
                                        :key="item.id"
                                        class="grey--text"
                                    >
                                        <td>
                                            <nuxt-link :to="'/admins/book-requests/' + item.id" class="grey--text" v-if="item.appliedBooks">{{ item.appliedBooks }}</nuxt-link>
                                        </td>
                                        <td class="text-center" v-if="item.appliedBooks">{{ item.appliedBooks.availableCopies }}</td>
                                    </tr>
                                </tbody>
                                </template>
                            </v-simple-table>
                            </template>
                    </v-col>
                </v-row>
                </v-container>
        </v-item-group>
    </main>
</template>
<script>
import { mapGetters, mapActions } from "vuex"
export default {
    middleware: ['auth', 'isAdmin'],
    components: {},
    data(){
        return {
            loading: false,
            search: null,
            books: [ 
                {title: 'Purpose driven life', availebleCopies: 10, id: '121313311'},
                {title: 'Purpose driven life', availebleCopies: 10, id: '121313331'},
                {title: 'Purpose driven life', availebleCopies: 10, id: '121313371'},
                {title: 'Purpose driven life', availebleCopies: 10, id: '121313361'},
            ]
        }
    },
    computed: {
        ...mapGetters({
            'bookRequests': 'administration/bookRequests'
        })
    },
    methods:{
        ...mapActions({
            'getAllBookRequests': 'administration/getAllBookRequests'
        })
    },
    mounted(){
        this.getAllBookRequests()
    }
}
</script>
<style scoped>
a{
    text-decoration: none !important;
}
.table-width{
    width: 100% !important;
    background: red !important;
}
</style>