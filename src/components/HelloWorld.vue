<template>
  <v-app id="inspire">
    <!--<v-navigation-drawer
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-view-dashboard</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-settings</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    -->
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="top" justify="center">
          <v-col>
            <v-row>
              <v-col>
                <v-card class="mx-auto" outlined>
                  <v-list-item three-line>
                    <v-list-item-content>
                      <div class="overline mb-4">OVERLINE</div>
                      <v-list-item-title class="headline mb-1">Books</v-list-item-title>
                      <v-simple-table height="450px">
                        <template v-slot:default>
                          <thead>
                            <tr>
                              <th class="text-left">ID</th>
                              <th class="text-left">Title</th>
                              <th class="text-left">Author</th>
                              <th class="text-left">Rented</th>
                              <th class="text-left">Reader</th>
                            </tr>
                          </thead>
                          <tbody>
                            <tr v-for="(item,keyb) in books" v-bind:key="keyb">
                              <td>{{ item.bookCID }}</td>
                              <td>{{ item.titleC }}</td>
                              <td>{{ item.authorC }}</td>
                              <td>{{ item.rented}}</td>
                              <td>{{ item.rentedbyReader}}</td>
                            </tr>
                          </tbody>
                        </template>
                      </v-simple-table>
                    </v-list-item-content>
                  </v-list-item>

                  <v-card-actions></v-card-actions>
                </v-card>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-card class="mx-auto" outlined>
                  <v-list-item three-line>
                    <v-list-item-content>
                      <div class="overline mb-4">OVERLINE</div>
                      <v-list-item-title class="headline mb-1">Rent Book</v-list-item-title>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="bookIDSource" label="Title" ></v-text-field>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="readerIDSource" label="Reader ID" ></v-text-field>
                        </v-col>
                      </v-row>
                    </v-list-item-content>
                  </v-list-item>

                  <v-card-actions>
                    <v-btn text v-on:click="rentbookMeth">Rent Book</v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-col>

          <v-col>
            <v-row>
              <v-col>

             
            <v-card class="mx-auto" outlined>
              <v-list-item three-line>
                <v-list-item-content>
                  <div class="overline mb-4">OVERLINE</div>
                  <v-list-item-title class="headline mb-1">Readers</v-list-item-title>
                  <v-simple-table height="450px">
                    <template v-slot:default>
                      <thead>
                        <tr>
                          <th class="text-left">ID</th>
                          <th class="text-left">Name</th>
                          <th class="text-left">Surname</th>
                        </tr>
                      </thead>
                      <tbody>
                        <tr v-for="(item,keyb) in readers" v-bind:key="keyb">
                          <td>{{ item.readerID }}</td>
                          <td>{{ item.name }}</td>
                          <td>{{ item.surname }}</td>
                        </tr>
                      </tbody>
                    </template>
                  </v-simple-table>
                </v-list-item-content>
              </v-list-item>

              <v-card-actions></v-card-actions>
            </v-card>
             </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-card class="mx-auto" outlined>
                  <v-list-item three-line>
                    <v-list-item-content>
                      <div class="overline mb-4">OVERLINE</div>
                      <v-list-item-title class="headline mb-1">Return Book</v-list-item-title>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="returnBookTitle" label="Title" ></v-text-field>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="readerIDSource" label="Reader ID" ></v-text-field>
                        </v-col>
                      </v-row>
                    </v-list-item-content>
                  </v-list-item>

                  <v-card-actions>
                    <v-btn text v-on:click="returnbookMeth">Return Book</v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-col>
          <v-col>
            <v-row>
              <v-col>
                <v-card class="mx-auto" outlined>
                  <v-list-item three-line>
                    <v-list-item-content>
                      <div class="overline mb-4">OVERLINE</div>
                      <v-list-item-title class="headline mb-1">Add Book</v-list-item-title>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="titleSource" label="title" ></v-text-field>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="authorSource" label="author" ></v-text-field>
                        </v-col>
                      </v-row>
                    </v-list-item-content>
                  </v-list-item>

                  <v-card-actions>
                    <v-btn text v-on:click="addBookMeth">Add Book</v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-card class="mx-auto" outlined>
                  <v-list-item three-line>
                    <v-list-item-content>
                      <div class="overline mb-4">OVERLINE</div>
                      <v-list-item-title class="headline mb-1">Add Reader</v-list-item-title>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="nameSource" label="name" ></v-text-field>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col>
                          <v-text-field v-model="surnameSource" label="surname" ></v-text-field>
                        </v-col>
                      </v-row>
                    </v-list-item-content>
                  </v-list-item>

                  <v-card-actions>
                    <v-btn text v-on:click="addReaderMeth">Add Reader</v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
import Vue from "vue";
import VueRouter from "vue-router";
import axios from "axios";

Vue.use(VueRouter);

export default {
  props: {
    source: String
  },
  data() {
    return {
      drawer: null,
      books: "",
      readers: "",
      titleSource: "",
      authorSource: "",
      keyb: 0,
      nameSource: "",
      surnameSource: "",
      bookIDSource: "",
      readerIDSource: "",
      roboczabook:"",
      returnBookTitle:""
    };
  },
  created() {
    this.$vuetify.theme.dark = true;
    axios
      .get("https://localhost:44381/api/BookCs")
      .then(res => (this.books = res.data));
    axios
      .get("https://localhost:44381/api/Readers")
      .then(res => (this.readers = res.data));
  },
  methods: {
    addBookMeth: function addbook() {
      axios.post("https://localhost:44381/api/BookCs", {
        titleC: this.titleSource,
        authorC: this.authorSource,
        rented: false,
        rentedbyReader: 0,
        rentData: "0001-01-01T00:00:00",
        dropOfData: "0001-01-01T00:00:00",
        aliasofReader: null
      });
      this.$forceUpdate();
      axios
        .get("https://localhost:44381/api/BookCs")
        .then(res => (this.books = res.data));
      this.keyb += 1;
    },
    addReaderMeth: function addreader() {
      axios.post("https://localhost:44381/api/Readers", {
        name: this.nameSource,
        surname: this.surnameSource,
        books: null,
        alias: "Ewa Danielska"
      });
      
      this.$forceUpdate();

     axios
        .get("https://localhost:44381/api/Readers")
        .then(res => (this.readers = res.data));
     // this.keyb += 1;
    },
    rentbookMeth: function rentbook(){
      
      
      for(var m=0; m < this.books.length; m++){
        //let i;
        // console.log("trafiony")
        // console.log(this.books[m].titleC)
        // console.log(this.bookIDSource)
        if(this.books[m].titleC===this.bookIDSource){
       this.roboczabook=this.books[m];
       console.log("trafiony")
       this.roboczabook.rented=true;
       var Readerint=parseInt(this.readerIDSource)
       this.roboczabook.rentedbyReader=Readerint;

        }
        
        
      }
      var num=this.roboczabook.bookCID;
      console.log(this.roboczabook);
      console.log(this.roboczabook.titleC);
      console.log(num);
      var adres="https://localhost:44381/api/BookCs/"+num;
      console.log(adres);
      axios.put("https://localhost:44381/api/BookCs/"+num,this.roboczabook);
      this.$forceUpdate(); 

      /*axios
        .get("https://localhost:44381/api/BookCs")
        .then(res => (this.books = res.data));
        
      this.keyb += 1;*/
    },
    returnbookMeth:function returnbook(){
       for(var m=0; m < this.books.length; m++){
        //let i;
        // console.log("trafiony")
        // console.log(this.books[m].titleC)
        // console.log(this.bookIDSource)
        if(this.books[m].titleC===this.returnBookTitle){
       this.roboczabook=this.books[m];
       console.log("trafiony")
       this.roboczabook.rented=false;
      
       this.roboczabook.rentedbyReader=0;

        }
        
        
      }
      var num=this.roboczabook.bookCID;
      console.log(this.roboczabook);
      console.log(this.roboczabook.titleC);
      console.log(num);
      var adres="https://localhost:44381/api/BookCs/"+num;
      console.log(adres);
      axios.put("https://localhost:44381/api/BookCs/"+num,this.roboczabook);
      this.$forceUpdate(); 
    }
  }
};
</script>