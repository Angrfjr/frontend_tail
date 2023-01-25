<template>
    <div>
      <div class="field">
        <label class="label">Nama</label>
        <div class="control">
          <input
            class="input"
            type="text"
            placeholder="Masukkan Data"
            v-model="nama"
          />
        </div>
      </div>
      
      <div class="field">
        <label class="label">Umur</label>
        <div class="control">
          <input
            class="input"
            type="text"
            placeholder="Masukkan Data"
            v-model="umur"
          />
        </div>
      </div>

      <div class="field">
        <label class="label">NIK</label>
        <div class="control">
          <input
            class="input"
            type="text"
            placeholder="Masukkan Data"
            v-model="nik"
          />
        </div>
      </div>

      <div class="field">
        <label class="label">Alamat</label>
        <div class="control">
          <input
            class="input"
            type="text"
            placeholder="Masukkan Data"
            v-model="alamat"
          />
        </div>
      </div>

      <div class="field">
        <label class="label">Status</label>
        <div class="control">
          <input
            class="input"
            type="text"
            placeholder="Masukkan Data"
            v-model="status"
          />
        </div>
      </div>
      <p></p>
      <div class="control">
        <button class="button is-success button is-info is-small text-white bg-green-500 hover:bg-gray-400 focus:outline-none focus:ring-4 focus:ring-blue-300 font-medium rounded-full text-sm px-2 py-1 text-center mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800" @click="createUsers">Create</button>
        <span class="mx-1"></span>
      </div>
    </div>
  </template>
   
  <script>
  // import axios
  import axios from "axios";
 
  export default {
    name: "AddProduct",
    data() {
      return {
        nama: "",
        umur: "",
        nik:"",
        alamat:"",
        status:"",
      };
    },
    methods: {
      // Create New product
      async createUsers() {
        try {
          await axios.post("http://localhost:5000/users", {
            nama: this.nama,
            umur: this.umur,
            nik: this.nik,
            alamat: this.alamat,
            status: this.status
          });
          this.nama = "";
          this.umur = "";
          this.nik ="";
          this.alamat = "";
          this.status =""
          this.$router.push("/");
        } catch (err) {
          console.log(err);
        }
      },
    },
  };
  </script>
  
  <style>
  </style>