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
      <div class="user" v-for="user in filteredUsers" :key="user.token" :class="{ selected: selectedUsers.includes(user.username) ? true : false }" @click="toggleSelected(user.username)">
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
          {{ messageBouton }}
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
      selectedUsers: [],
      messageBouton: "Ouvrir la conversation (0)",
    };
  },
  methods: {
    ...mapActions(["createOneToOneConversation","createManyToManyConversation"]),

    openConversation() {
      let promise;
      console.log(this.selectedUsers)
      if(this.selectedUsers.length>1)
      {
        promise=this.createManyToManyConversation(this.selectedUsers);
      }
      else
      {
         promise=this.createOneToOneConversation(this.selectedUsers[0]);
      }
      
      this.messageBouton = "Ouverture de la conversation...";
      this.selectedUsers = [];
      promise.finally(() => {
        console.log("Conversation ouverte !");
      });
    },

     toggleSelected(username) {
      console.log(this.selectedUsers);
      if(!this.selectedUsers.includes(username)){
        this.selectedUsers.push(username);
        this.isSelected = true;
      }
      else{
        var index = this.selectedUsers.indexOf(username);
        if(index > -1){
          this.selectedUsers.splice(index, 1);
        }
      }
      this.messageBouton = "Ouvrir la conversation (" + this.selectedUsers.length + ")";
    },

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