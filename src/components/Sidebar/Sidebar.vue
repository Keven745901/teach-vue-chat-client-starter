<template>
  <div class="sidebar">
    <div class="user">
      <div class="user-picture">
        <img :src="user.picture_url" class="ui circular image" />
      </div>

      <div class="user-info">
        <div class="user-info-pseudo">{{ user.username }}</div>

        <div class="user-info-status ui simple dropdown">
          <div class="available text">
            En ligne
          </div>
          <i class="dropdown icon"> </i>
          <div class="menu">
            <div class="item" @click="deauthenticate">
              <i class="logout icon"> </i>
              Déconnexion
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="menu">
      <div class="blue button" @click="openCommunity">
        <i class="users icon"> </i>
        <br />
        <span>Communauté</span>
      </div>
      <div v-if="true" class="blue button" @click="openMessageSearch">
        <i class="search icon"> </i>
        <br />
        <span>Messages</span>
      </div>
       <div v-if="true" class="blue button" @click="openInfos">
        
        <br />
        <span>Infos</span>
      </div>

    </div>
    <div class="conversations">
      <div
      v-for="c in listeConversations" :key="c.id"
        class="conversation selected"
        :title="c.title"
        @click="openConversation(c.id)"
      >
        <a class="avatar">
          <img src="https://source.unsplash.com/FUcupae92P4/100x100" />
        </a>
        <div class="content">
          <div class="metadata">
            <div class="title">{{(c.participants)}}</div>
            <span class="time">{{c.updated_at}}</span>
          </div>
          <div class="text">{{c.message}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import router from "@/router";
import { mapActions, mapGetters } from "vuex";

export default {
  name: "Sidebar",
  data() {
    return {
      search: "",
      nomsConversation: [],
      search: ""
    };
  },
  methods: {
    ...mapActions(["deauthenticate"]),
    openCommunity() {
      router.push({ name: "Community" });
    },
    openInfos() {
      router.push({ name: "Informations" });
    },
    openMessageSearch() {
      router.push({ name: "Search" });
    },
    openConversation(id) {
      router.push({ name: "Conversation", params: { id } });
    },
    addnomConversation(conversation){
      var nomConversation="";
      conversation.participants.forEach(element => {
        nomConversation=nomConversation+element+"";
      });
      this.nomsConversation.push(nomConversation);
    }
  },
  computed: {
    ...mapGetters(["user", "conversations"]),
    listeConversations: function(){
      var convs = [];
      this.conversations.forEach(element => {
        convs.push({ updated_at: element.updated_at.substring(11, 19), id: element.id, participants: element.participants[0] + ", " + element.participants[1], message: element.message });
      });
      return convs;
    }
  }
};
</script>

<style scoped src="./Sidebar.css" />