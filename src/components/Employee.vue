<template>
  <div>
    <p>Employee</p>

    <div class="input-group mb-3">
      <span class="input-group-text" id="inputGroup-sizing-default"
        >Employee ID</span
      >
      <input
        type="text"
        class="form-control"
        aria-label="Sizing example input"
        v-model="info.EmployeeID"
      />
    </div>
    <div class="input-group mb-3">
      <span class="input-group-text" id="inputGroup-sizing-default"
        >First Name</span
      >
      <input
        type="text"
        class="form-control"
        aria-label="Sizing example input"
        v-model="info.firstName"
      />
    </div>
    <div class="input-group mb-3">
      <span class="input-group-text" id="inputGroup-sizing-default"
        >Last Name</span
      >
      <input
        type="text"
        class="form-control"
        aria-label="Sizing example input"
        v-model="info.LastName"
      />
    </div>

    <!-- <div>
      <input
        type="radio"
        class="btn-check"
        name="options"
        id="option1"
        autocomplete="off"
        v-model="info.Gender"
        value="Male"
      />
      <label class="btn btn-outline-primary" for="option1">Male</label>

      <input
        type="radio"
        class="btn-check"
        name="options"
        id="option2"
        autocomplete="off"
        v-model="info.Gender"
        value="Female"
      />
      <label class="btn btn-outline-primary" for="option2">Female</label>
    </div> -->

    <div
      class="from-check mb-3"
      v-for="(data, index) in gender"
      v-bind:key="index"
    >
      <input
        type="radio"
        class="btn-check"
        name="options"
        :id="index"
        autocomplete="off"
        v-model="info.Gender"
        value="Male"
      />
      <label class="btn btn-outline-primary" :for="index">{{
        data.label
      }}</label>
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="inputGroup-sizing-sm">Time In</span>
      <b-form-timepicker v-model="info.TimeIn" locale="en"></b-form-timepicker>
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="inputGroup-sizing-sm">Time Out</span>
      <b-form-timepicker v-model="info.TimeOut" locale="en"></b-form-timepicker>
    </div>

    <div>
      <button type="button" class="btn btn-primary" v-on:click="save">
        Save
      </button>
    </div>

    <!--<div :hidden="!show">
      <h3>Employee ID : {{ info.EmployeeID }}</h3>
      <h3>First Name : {{ info.firstName }}</h3>
      <h3>Last Name : {{ info.LastName }}</h3>
      <h3>Gender : {{ info.Gender }}</h3>
      <h3>Time : {{ info.TimeIn }} - {{ info.TimeOut }}</h3>
      <h3>
        Active :
        <span v-if="info.Active" v-bind:style="{ color: 'green' }">
          Actice
        </span>
        <span v-else v-bind:style="{ color: 'red' }"> Non Actice </span>
      </h3>
    </div> -->

    <!--<div :hidden="!show" v-for="(data, index) in employeeInfo" :key="index">
      <h3>Employee ID : {{ data.EmployeeID }}</h3>
      <h3>First Name : {{ data.firstName }}</h3>
      <h3>Last Name : {{ data.LastName }}</h3>
      <h3>Gender : {{ data.Gender }}</h3>
      <h3>Time : {{ data.TimeIn }} - {{ data.TimeOut }}</h3>
      <h3>
        Active :
        <span v-if="data.Active" v-bind:style="{ color: 'green' }">
          Actice
        </span>
        <span v-else v-bind:style="{ color: 'red' }"> Non Actice </span>
      </h3>
    </div> -->

    <div :hidden="!show">
      <b-table striped hover :items="employeeInfo"></b-table>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "Employee",
  data() {
    return {
      info: {
        EmployeeID: null,
        FirstName: null,
        LastName: null,
        Gender: null,
        TimeIn: null,
        TimeOut: null,
        Active: false,
      },
      show: false,
      gender: [
        {
          label: "Male",
          value: "M",
        },
        {
          label: "Female",
          value: "F",
        },
      ],
      employeeInfo: [],
    };
  },
  methods: {
    save() {
      this.employeeInfo.push(this.info);
      this.checkActiveTime();
      this.show = true;
      this.info = {
        EmployeeID: null,
        FirstName: null,
        LastName: null,
        Gender: null,
        TimeIn: null,
        TimeOut: null,
        Active: false,
      };
    },
    checkActiveTime() {
      const today = new Date();
      const time = moment(today, "HH:mm");
      if (
        moment(this.info.TimeIn, "HH:mm").isBefore(time) &&
        moment(time).isBefore(this.info.TimeOut, "HH:mm")
      ) {
        this.info.Active = true;
      } else {
        this.info.Active = false;
      }
    },
  },
};
</script>

<style>
</style>