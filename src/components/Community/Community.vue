<template>
  <div class="community">
    <div class="filter">
      <div class="ui fluid search">
        <div class="ui icon input">
          <input
            class="prompt"
            type="text"
            placeholder="Rechercher un utilisateur"
            v-model="search"
          />
          <i class="search icon"></i>
        </div>
        <div class="results"></div>
      </div>
    </div>
    <div class="users">
      <div class="user" v-for="user in filteredUsers" :key="user.token">
        <img :src="user.picture_url" /><span
          class=""
          >{{ user.username }}</span
        >
      </div>
    </div>

    <div class="actions">
      <button class="ui primary big button" @click="openConversation">
        <i class="conversation icon"></i>
        <span>
          Ouvrir la conversation (2)
        </span>
      </button>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Community",
  data() {
    return {
      search: "",
    };
  },
  methods: {
    ...mapActions(["createOneToOneConversation"]),

    openConversation() {
      let promise = this.createOneToOneConversation("Alice");

      promise.finally(() => {
        console.log("Conversation ouverte !");
      });
    }
  },
  computed: {
    ...mapGetters(["users"]),
    filteredUsers: function() {
      var u = [];
      if(this.users !== null){
        this.users.forEach(element => {
        if(element.username.toLowerCase().includes(this.search.toLowerCase()))
        {
          u.push(element);
        }
      });
      }
    return u
    },
  }
};
</script>

<style src="./Community.css" scoped />