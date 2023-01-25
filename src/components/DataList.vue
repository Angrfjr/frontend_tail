<template>
    <div>
      <h1 class="bg-gray-700 mb-4 text-4xl text-center font-mono Liberation Mono leading-none tracking-tight text-green-600 font-bold px-3 py-2 md:text-4xl lg:text-4xl dark:text-white">PENCATATAN PENDUDUK</h1>
      <nav class="bg-white border-gray-400">
      <table class="w-full text-sm text-left text-black-400 dark:text-gray-400">
          <div class="sm:rounded-lg mb-10">
            <router-link :to="{ name: 'Create' }" class="text-white bg-blue-700 hover:bg-blue-800 focus:outline-none focus:ring-4 focus:ring-blue-300 font-medium rounded-full text-sm px-5 py-2.5 text-center mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Tambah Data</router-link>
            <div class="mx-4 "></div>
          </div>
          <div class="mx-4 "></div>
            <p></p>
          <table class="w-full text-sm text-left text-black dark:text-gray-400">
            <thead class="text-xs text-white uppercase bg-gray-700 dark:bg-gray-700 dark:text-gray-400">
              <tr>
                <th class="text-center px-6 py-3">Nama</th>
                <th class="text-center px-6 py-3">Umur</th>
                <th class="text-center px-6 py-3">NIK</th>
                <th class="text-center px-6 py-3">Alamat</th>
                <th class="text-center px-6 py-3">Status</th>
                <th class="text-center px-6 py-3">Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr class="bg-white border-b dark:bg-gray-900 dark:border-gray-700" v-for="item in items" :key="item.id">
                <td class="text-center">{{ item.nama }}</td>
                <td class="text-center">{{ item.umur }}</td>
                <td class="text-center">{{ item.nik }}</td>
                <td class="text-center">{{ item.alamat }}</td>
                <td class="text-center">{{ item.status }}</td>
                <td class="text-center">
                  <router-link
                    :to="{ name: 'Edit', params: { id: item.id } }"
                    class="button is-info bg-blue-600 rounded px-2 py-1 text-white hover:bg-red-400"
                    >Edit</router-link>
                  <span class="mx-1"></span>
                  <a
                    type="button" class="button is-success bg-red-600 rounded px-2 py-1 text-white hover:bg-red-400"
                    href=# @click="deleteUsers(item.id)"
                    >Delete</a>
                </td>
              </tr>
            </tbody>
          </table>
      </table>
    </nav>
    </div>
  </template>
   
  <script>
  // import axios
  import axios from "axios";
   
  export default {
    name: "DataList",
    data() {
      return {
        items: [],
      };
    },
   
    created() {
      this.getUsers();
    },
   
    methods: {
      // Get All Products
      async getUsers() {
        try {
          const response = await axios.get("http://localhost:5000/users");
          this.items = response.data;
        } catch (err) {
          console.log(err);
        }
      },
   
      // Delete Product
      async deleteUsers(id) {
        try {
          await axios.delete(`http://localhost:5000/users/${id}`);
          this.getUsers();
        } catch (err) {
          console.log(err);
        }
      },
    },
  };
  </script>
   
  <style>
  </style>
