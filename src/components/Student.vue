<template lang="">
    <div>
        <form @submit="checkForm">

            <p v-if="conditions.length">
            <b> Please Input your infomation </b>
            <ul>
                <li v-for="error in conditions" :key="error" style="color: red"> {{ error }}</li>
            </ul>
            </p>


            <input type="text" v-model="id" placeholder="Student ID" style="margin-right:10px">
            <input type="checkbox" v-model="gender" value="Male"> Male
            <input type="checkbox" v-model="gender" value="Female"> Female
            <br>
            <input type="text" v-model="fname" placeholder="FirstName" style="margin-right:10px" required>
            <input type="text" v-model="lname" placeholder="LastName" style="margin-right:10px" required>
            <br>
            <textarea v-model="introduce" placeholder="Introduce yourself"></textarea>
            <br>
            <input type="radio" id="one" value="one" v-model="picked"/> จบแล้ว
            <input type="radio" id="two" value="two" v-model="picked"/> ยังไม่จบ

            <select v-model="Selected">
                <option value="">Select</option>
                <option 
                v-for="option in options" 
                :key="option" 
                v-bind:value="option.value">
                {{option.text}}
                </option>
            </select>

            <br>
            <input type="submit" value="Submit" >

        </form>
    </div>
</template>
<script>
import Router from "vue-router"

const router = new Router({
    mode: "history",
})

export default {
    name : "Student",
    data() {
        return{
            id: null,
            gender: [],
            fname: null,
            lname: null,
            introdude:null,
            picked: null,
            selected: "",
            options:[
                {text: "ชั้นปีที่ 1",vale: "1"},
                {text: "ชั้นปีที่ 2",vale: "2"},
                {text: "ชั้นปีที่ 3",vale: "3"},
                {text: "ชั้นปีที่ 4",vale: "4"},
            ],
            conditions: [],
        }
    },
    methods: {
        checkForm(e) {
            if(!this.id)
            {
                this.conditions.push("*Please input your Student ID*");
            }
            else
            {
                router.push(`/page1/${this.id}`)
                router.go()
            }
            e.preventDefault();
        }
    }
}
</script>
<style lang="">
    
</style>