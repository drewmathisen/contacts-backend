<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="contact in contacts" v-bind:key="contact.id">
      <p>{{ contact.first_name }} {{ contact.last_name }}</p>
      <!-- <p>{{ contact.email }}</p>
      <p>{{ contact.phone_number }}</p> -->
      <img v-bind:src="contact.image" v-bind:alt="contact.last_name" />
      <hr />
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Your Contacts!",
      contacts: [],
    };
  },
  created: function () {
    this.indexContacts();
  },
  methods: {
    indexContacts: function () {
      console.log("in IndexContacts");
      axios.get("http://localhost:3000/contacts").then((response) => {
        console.log(response.data);
        this.contacts = response.data;
      });
    },
    showContact: function () {
      console.log("in show function");
    },
  },
};
</script>
