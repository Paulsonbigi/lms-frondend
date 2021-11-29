<template>
    <main>
        <v-item-group active-class="primary">
            <v-container>
                <div class="text-h6 text-left font-weight-medium grey--text mb-10 text-capitalize">{{bookTitle}}</span></div>
                <v-row>
                    <v-col  cols="12" md="6">
                        <v-row>
                            <v-col cols="12" md="4">
                                <div class="fill-height d-flex justify-center flex-column align-center" >
                                    <img src="/svg/login.svg" width="100%" alt="Login image"/>
                                </div>
                            </v-col>
                            <v-col cols="12" md="8">
                                <div class="grey--text mb-3">Author: <strong>Myles Munroe</strong></div>
                                <div class="grey--text mb-3">Published on: <strong>21st of August, 2021</strong></div>
                                <div class="grey--text mb-3">ISBN number: <strong>9875679679</strong></div>
                                <div class="grey--text mb-3">Available copies: <strong>10</strong></div>
                                <v-row>
                                    <v-col cols="6">
                                        <div>Borrow book for:</div>
                                    </v-col>
                                    <v-col>
                                        <div class="grey--text"> 
                                            <v-select
                                                :items="items"
                                                label="Days"
                                                solo
                                                :required="true"
                                                ></v-select>
                                        </div>
                                    </v-col>
                                </v-row>
                                <div class="grey--text mb-6">Book description:
                                    <p class="text-justify text--disabled">This is the description of this book. This is the description of this book. This is the description of this book.This is the description of this book This is the description of this book. This is the description of this book. This is the description of this book.This is the description of this book</p>
                                </div>
                                <v-btn @click="borrowBook" color="primary" block class="px-12 w-full bg-primary ">Borrow Book</v-btn>
                            </v-col>
                        </v-row>
                    </v-col>
                </v-row>
                <v-dialog
                    v-model="dialog"
                    max-width="290"
                    >
                    <v-card>
                        <v-card-title class="text-h5 text-center primary--text">
                        Borrow Book
                        </v-card-title>

                        <v-card-text class="text-center">
                       Are you sure you want to borrow this book for 2 days
                        </v-card-text>

                        <v-card-actions>
                        <v-spacer></v-spacer>
                            <v-btn @click="confirmBorrow" color="primary" depressed block class="px-12 w-full bg-primary ">Confirm</v-btn>
                        </v-card-actions>
                    </v-card>
                    </v-dialog>
            </v-container>
        </v-item-group>
    </main>
</template>
<script>
export default {
  data(){
      return {
          bookTitle: 'Purpose Driven Life',
          items: ['1 day', '2 days', '3 days'],
          dialog: false
      }
  },
  methods: {
      borrowBook(){
          this.dialog = true;
      },
      confirmBorrow(){
          this.dialog = false;
      }
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