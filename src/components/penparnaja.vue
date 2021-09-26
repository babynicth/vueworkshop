<template>
    <div id="bg" class="color">
        <img :src="url" width="15%" height="15%" />
        <p>ห่มจีวรคือเป็นพระ - ห่มผ้าด้วยนะคือเป็นห่วง</p>
        <div class="input-group mb-3">
            <span class="input-group-text" id="inputGroup-sizing-sm">ID</span>
            <input type="text" class="form-control" aria-label="Sizing example input" v-model="info.id">
        </div>
        <div class="input-group mb-3">
            <span class="input-group-text" id="inputGroup-sizing-sm">FirstName</span>
            <input type="text" class="form-control" aria-label="Sizing example input" v-model="info.firstName">
        </div>
        <div class="input-group mb-3">
            <span class="input-group-text" id="inputGroup-sizing-sm">LastName</span>
            <input type="text" class="form-control" aria-label="Sizing example input" v-model="info.lastName">
        </div>


        <button type="button" class="btn btn-primary" @click="save">Save</button>

        <div :hidden="!show" v-for="(data,index) in myfriendInfo" :key="index">
            <span>myfriend ID :{{data.id}}</span>
            <span>First Name :{{data.firstName}}</span>
            <span>Last Name :{{data.lastName}}</span>
        </div> 

        <div :hidden="!show">
            <b-table striped hover :items="myfriendInfo"></b-table>
        </div>

    </div>
    
</template>

<script>
export default {
    name: "myfriend",
    data(){
        return{
            url: "https://pbs.twimg.com/media/EeKgIC3UEAQ7YMV.jpg",
            info :{
                id : null,
                firstName : null,
                lastName : null,
            },
            show : false,
            myfriendInfo : []
        }
    },
    methods:{
        save(){
            this.myfriendInfo.push(this.info);
            this.show = true;
            this.info = {
                id : null,
                firstName : null,
                lastName : null,
            };
            
        },
    }
}
</script>

<style>
.color {
  background-color: lightblue;
  color: black;
}
</style>