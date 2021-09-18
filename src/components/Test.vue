<template>
  <div id="test" :class="color">

   <div class="input-group input-group-sm mb-3">
      <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-sm">Color</span>
      </div>
      <input
        type="text"
        class="form-control"
        aria-label="Sizing Example Input"
        v-model="colorBG"
      />
    </div>
    <div v-bind:style="{ background: colorBG, fontSize: fontSize + 'px' }">color : {{ colorBG }} </div>
    <br />
    <br />

<div class="input-group input-group-sm mb-3">
        <span class="input-group-text" id="inputGroup-sizing-sm">User</span>
        <input type="text" class="form-control" aria-label="Sizing example input" v-model="userName">
    </div>

    <div class="input-group mb-3">
        <span class="input-group-text" id="inputGroup-sizing-default">Password</span>
        <input type="text" class="form-control" aria-label="Sizing example input" v-model="userpass">
    </div>

    <div>
        shown<br>
        user: {{userName}} <br>
        password: {{userpass}} <br>
    </div>


    <div class="card">
      <div class="class-header">
        ชื่อ {{ myInfo.myName }}
        <button type="button" class="btn btn-primary" v-on:click="myShownInfo">
          {{ labelBotton }}
        </button>
      </div>
      <div class="class-body" :hidden="!hideShown">
        <p>myNickName: {{ myInfo.myNickName }}</p>
        <p>myStudentID: {{ myInfo.myStudentID }}</p>
      </div>
    </div>
    <p>v-on v-bind</p>

    <button
      type="button"
      class="btn btn-danger"
      v-on:click="alertMsg('D', 'F', $event)"
    >
      NCT
    </button>
    <button type="button" class="btn btn-primary" v-on:click="alertMsg">
      DREAM
    </button>
    <button type="button" class="btn btn-light" v-on:dblclick="alertMsgDB">
      กด!!
    </button>
    <p>MarkMin</p>
    <p>{{ shown }}</p>
    <img v-bind:src="url" width="50%" height="50%" />
    <img :src="url" width="50%" height="50%" />
    <p>Name : {{ fName }}</p>

    <span /> celsius : {{ celsius }} <span /> fahrenheit : {{ fahrenheit }}

    <p>{{ shown }}</p>
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      fName: "MARK & JAEMIN",
      imgName: "MarkMin",
      url: "https://i.pinimg.com/originals/a4/7c/58/a47c58c67dfa0ce3d9801019effc1bda.jpg",
      color: "tmp2",
      celsius: 30,
      dataPuma: ["หัว", "ก้อย"],
      text: "click",

      myInfo: {
        myName: "Nichda Thongmaim",
        myNickName: "Mameaw",
        myStudentID: "6130203314",
      },
      hideShown: true,

      userName : null,
      userpass: null,
      colorBG : null,

    };
  },
  computed: {
    fahrenheit() {
      let result = this.celsius * 1.8 + 32;
      return result;
    },
    random() {
      return Math.random() > 0.5 ? 1 : 0;
    },
    shown() {
      return this.dataPuma[this.random];
    },
    labelBotton() {
      return this.hideShown ? "Hide" : "Shown";
    },
  },
  methods: {
    alertMsg(p1, p2, e) {
      alert(`You ${e.type} the button at ${e.clientX}, ${e.clientY}`);
      alert(`parameter ${p1}, ${p2}`);
    },
    alertMsgDB() {
      console.log("Hello, Nichada Thongmaim");
    },
    myShownInfo() {
      this.hideShown = !this.hideShown;
    },
  },
};
</script>

<style>
.tmp {
  background-color: lightblue;
  color: black;
}
.tmp2 {
  background: lightblue;
  color: black;
}
</style>