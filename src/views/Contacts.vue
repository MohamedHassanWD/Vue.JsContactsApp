<template>
  <div class="about">
    <h1 style="text-align:center">Your Contacts</h1>
    <a-input
      placeholder="Search by Name"
      style="width: 100%"
      v-model="searchQuery"
      @change="onSearch"
    />
    <br>
    <br>
    <p v-if="searchQuery !== null && searchQuery !== ''">Search Results for: {{searchQuery}}</p>
    <p>
      <small>
        <strong>Contacts: {{filteredContacts.length}}</strong>
      </small>
    </p>
    <br>
    <div v-if="filteredContacts.length >= 1">
      Order By:
      <a-select
        style="float:right"
        defaultValue="nameAsc"
        @change="orderContacts"
        v-model="orderBy"
      >
        <a-select-option value="nameAsc">Name (Ascending)</a-select-option>
        <a-select-option value="nameDesc">Name (Descending)</a-select-option>
      </a-select>
    </div>

    <br>
    <br>

    <a-card v-for="(contact, index) in filteredContacts" :key="index">
      <h3>{{contact.name}}</h3>
      <p>{{contact.address}}</p>
      <p>
        <em>
          <a :href="'tel:'+contact.phone_number">{{contact.phone_number}}</a>
        </em>
      </p>
    </a-card>
  </div>
</template>

<script>
import axios from "axios";
function dynamicSort(property) {
  var sortOrder = 1;

  if (property[0] === "-") {
    sortOrder = -1;
    property = property.substr(1);
  }

  return function(a, b) {
    if (sortOrder == -1) {
      return b[property].localeCompare(a[property]);
    } else {
      return a[property].localeCompare(b[property]);
    }
  };
}
export default {
  data() {
    return {
      contacts: [],
      filteredContacts: [],
      searchQuery: "",
      orderBy: "nameAsc",
      errors: []
    };
  },
  mounted() {
    this.getContacts();
  },
  methods: {
    getContacts() {
      axios
        .get("http://www.mocky.io/v2/581335f71000004204abaf83")
        .then(response => {
          this.contacts = this.filteredContacts = response.data.contacts;
          this.orderContacts();
          // console.log(response.data.contacts);
        })
        .catch(error => {
          console.log(error);
        });
    },
    onSearch() {
      if (
        this.searchQuery == "" ||
        this.searchQuery == null ||
        this.searchQuery == undefined
      ) {
        this.getContacts();
      } else {
        this.filteredContacts = this.contacts.filter(contact => {
          return contact.name
            .toLowerCase()
            .includes(this.searchQuery.toLowerCase());
        });
      }
    },
    orderContacts() {
      switch (this.orderBy) {
        case "nameAsc":
          this.filteredContacts.sort(dynamicSort("name"));
          break;
        case "nameDesc":
          this.filteredContacts.sort(dynamicSort("-name"));
          break;
      }
    }
  }
};
</script>

<style scoped>
.contact {
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>
