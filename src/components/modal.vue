<template>
    <v-app>
        <div class="text-xs-center">
            <v-dialog
                    v-model="dialog"
                    width="500"
            >
                <v-btn
                        slot="activator"
                        color="red lighten-2"
                        dark
                >
                    Click Me
                </v-btn>

                <v-card>
                    <ul class="list" v-for="item in technicType" :key="item.name">
                        <li>
                            {{item.name}}
                            <span><input type="checkbox" :value="item.name" @click="hideItem(item.id)"></span>
                            <span><input type="checkbox" :value="item.name" v-model="checked"></span>
                        </li>
                    </ul>
                    <ul class="list" v-for="item in model" :key="item.name">
                        <li>
                            {{item.name}}
                            <span><input type="checkbox" :value="item.name" @click="deleteItem(item.id)"></span>
                            <span><input type="checkbox" :value="item.name" v-model="checked"></span>
                        </li>
                    </ul>
                    <ul class="list" v-for="item in technic" :key="item.name">
                        <li>
                            {{item.name}}
                            <span><input type="checkbox" :value="item.name" @click="sliceItem(item.id)"></span>
                            <span><input type="checkbox" :value="item.name" v-model="checked"></span>
                        </li>
                    </ul>

                    <v-divider></v-divider>

                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn
                                color="success"
                                flat
                                @click="getData"
                        >
                            Submit
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-dialog>
        </div>
    </v-app>
</template>

<script>
    const axios = require('axios');
    export default {
        name: "modal",
        data(){
            return{
                dialog: false,
                hidden: null,
                technicType: null,
                model: null,
                technic: null,
                checked: []
            }
        },
        methods:{
            getData1(){
                axios.get('https://api.myjson.com/bins/7y3fr')
                    .then(res => this.technicType = res.data);
                axios.get('https://api.myjson.com/bins/170i8s')
                    .then(res => this.model = res.data);
                axios.get('https://api.myjson.com/bins/1h4vj0')
                    .then(res => this.technic = res.data)
            },
            getData(){
                console.log(this.checked.map(item => console.log(item)))
            },
            hideItem(id){
                return this.technicType = this.technicType.filter(item => item.id !== id)
            },
            deleteItem(id){
                return this.model = this.model.filter(item => item.id !== id)
            },
            sliceItem(id){
                return this.technic = this.technic.filter(item => item.id !== id)
            }
        },
        created(){
            this.getData1();
        }
    }
</script>

<style scoped>
    .list{
        margin: 0;
        padding: 0;
        list-style-type: none;
    }
</style>