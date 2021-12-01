<template>
  <div class="wrapper">
    <div v-if="showForm" class="form">
      <div class="formitem">
        <legend>Email</legend>
        <input type="text" v-model="userInfo.email" />
      </div>
      <div class="formitem">
        <legend>First Name</legend>
        <input type="text" v-model="userInfo.firstName" />
      </div>
      <div class="formitem">
        <legend>Last Name</legend>
        <input type="text" v-model="userInfo.lastName" />
      </div>
      <div class="formitem">
        <legend>Phone</legend>
        <input type="text" v-model="userInfo.phone" />
      </div>
      <hr />
      <div class="guests">
        <span class="bolder">Guests</span>
        <button class="btn btn-submit" @click="addGuest">+</button>
         <input class="form-guest"
          v-for="(guest, index) in guests"
          type="text"
          v-model="guests[index]"
          :key="index"
        />
      </div>
      <hr />
      <button class="btn btn-success" @click="sendData">Send Data</button>
      <hr />
    </div>
    <div v-else>
      <h2 class="h2-center">All Done!</h2>
      <table class="table table-bordered">
        <tr>
          <td>Email</td>
          <td>{{ userInfo.email }}</td>
        </tr>
        <tr>
          <td>Name</td>
          <td>{{ userInfo.firstName }} {{ userInfo.lastName }}</td>
        </tr>
        <tr>
          <td>Phone</td>
          <td>{{ userInfo.phone }}</td>
        </tr>
        <tr>
          <td>Guests</td>
          <td>
            <ul class="list-group">
              <li
                class="group-item"
                v-for="(guest, index) in guests"
                :key="index"
              >
                {{ guest }}
              </li>
            </ul>
          </td>
        </tr>
      </table>
      <button class="btn btn-success back" @click="back">Back</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userInfo: {
        email: "",
        firstName: "",
        lastName: "",
        phone: "",
      },
      guests: [],
      newGuest: "",
      showForm: true,
    };
  },
  methods: {
    addGuest() {
      this.showInput = true;
      this.guests.push("");
    },
    sendData() {
      this.showForm = false;
    },
    back() {
       this.showForm = true;
    }, 
   }
 };
</script>

<style>
legend {
  font-size: 1rem;
  margin-bottom: 0;
  font-weight: 600;
}
button.back {
    display: block;
    margin-left: auto;
    margin-right: auto }

button.btn-submit {
  margin-left: 20px;
}
.table {
  margin: 0 auto;
  width: 350px !important;
}
.form-guest {
  margin-top: 10px;
}
.bolder {
  font-weight: 600;
}
.form {
  margin: 0 auto;
  width: 350px;
  margin-top: 50px;
}
.formitem {
  margin-bottom: 10px;
}
.h2-center {
  text-align: center;
  margin-top: 20px;
}
input {
  margin: 0 auto;
  width: 350px;
}
.list-group {
  margin-left: 20px;
}
</style>
