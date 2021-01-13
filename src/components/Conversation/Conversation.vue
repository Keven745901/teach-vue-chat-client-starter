<template>
  <div class="conversation" v-if="conversation">
    <div class="conversation-header">
           <img class="avatar" :src="findPicture(conversation)"/>
      <!-- <div class="avatar">
        <i class="ui users icon"></i>
      </div> -->

      <div class="title">
        <div class="ui compact">
          <i class="icon circle"></i>
          <span v-if="conversation.participants.length > 2">Groupe: {{ conversation.participants.join(" , ") }}</span>
          <span v-else>{{ conversation.participants[1] }}</span>
          <div class="ui simple dropdown item">
            <i class="vertical ellipsis icon"></i>

            <div class="menu">
              <div v-if="true" class="item">
                <i class="ui icon paint brush"></i>
                Modifier le thème
              </div>
              <div v-if="true" class="item">
                <i class="ui icon edit"></i>
                Modifier le titre
              </div>
              <div v-if="true" class="item">
                <i class="ui icon volume bell slash"></i>
                Mettre en sourdine
              </div>
              <div v-if="true" class="item">
                <i class="ui icon volume bell"></i>
                Rétablir les notifications
              </div>
              <div class="item" @click="groupPanel = !groupPanel">
                <i class="ui icon users"></i>
                Gérer les participants
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="conversation-container">
      <div class="conversation-main">
        <div class="conversation-body" id="scroll">
          <div class="wrapper">
            <div class="time">01:32:14</div>
            <div class="message mine">
              <!-- <div class="bubble top bottom">{{m.content}}</div> -->
              <div class="reacts"></div>
              <div class="controls">
                <i title="Supprimer" class="circular trash icon"></i
                ><i title="Editer" class="circular edit icon"></i
                ><i title="Répondre" class="circular reply icon"></i>
              </div>
            </div>
            <div class="time">01:32:14</div>
            <div class="message">
              <img
                title="Bob"
                src="https://source.unsplash.com/7omHUGhhmZ0/100x100"
              />
              <div class="bubble top bottom">Hello !</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="message">
              <img
                title="Alice"
                src="https://source.unsplash.com/mK_sjD0FrXw/100x100"
              />
              <div class="bubble top bottom">Coucou !</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="time">01:32:31</div>
            <div class="message mine">
              <div class="bubble top bottom">Vous allez bien ?</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Supprimer" class="circular trash icon"></i
                ><i title="Editer" class="circular edit icon"></i
                ><i title="Répondre" class="circular reply icon"></i>
              </div>
            </div>
            <div class="time">01:32:38</div>
            <div class="message">
              <img
                title="Alice"
                src="https://source.unsplash.com/mK_sjD0FrXw/100x100"
              />
              <div class="bubble top bottom">Oui ça va et toi ?</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="time">01:32:48</div>
            <div class="message mine">
              <div class="bubble top">Ca va super !</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Supprimer" class="circular trash icon"></i
                ><i title="Editer" class="circular edit icon"></i
                ><i title="Répondre" class="circular reply icon"></i>
              </div>
            </div>
            <div class="message mine">
              <div class="bubble middle">
                Je viens de découvrir ce nouveau chat
              </div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Supprimer" class="circular trash icon"></i
                ><i title="Editer" class="circular edit icon"></i
                ><i title="Répondre" class="circular reply icon"></i>
              </div>
            </div>
            <div class="message mine">
              <div class="bubble bottom">C'est vraiment chouette</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Supprimer" class="circular trash icon"></i
                ><i title="Editer" class="circular edit icon"></i
                ><i title="Répondre" class="circular reply icon"></i>
              </div>
            </div>
            <div class="time">01:33:32</div>
            <div class="message">
              <div class="bubble top">Oui je l'aime beaucoup aussi</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="message">
              <div class="bubble middle">
                <p class="reply_content">C'est vraiment chouette</p>
                On peut répondre à un message
              </div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="message">
              <img
                title="Bob"
                src="https://source.unsplash.com/7omHUGhhmZ0/100x100"
              />
              <div class="bubble bottom">Ou bien y réagir</div>
              <div class="reacts">
                <i title="Aimer" class="circular heart outline icon">1</i>
              </div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="message">
              <img
                title="Alice"
                src="https://source.unsplash.com/mK_sjD0FrXw/100x100"
              />
              <div class="bubble top bottom">
                On peut même éditer ou supprimer des messages !
              </div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="view">
              <img
                title="Vu par Bob à 01:35:50"
                src="https://source.unsplash.com/7omHUGhhmZ0/100x100"
              />
            </div>

            <div class="time">01:36:24</div>
            <div class="message mine">
              <div class="bubble top bottom">
                Et on peut voir qui a vu un message ou non ?
              </div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Supprimer" class="circular trash icon"></i
                ><i title="Editer" class="circular edit icon"></i
                ><i title="Répondre" class="circular reply icon"></i>
              </div>
            </div>
            <div class="time">01:36:31</div>
            <div class="message">
              <img
                title="Alice"
                src="https://source.unsplash.com/mK_sjD0FrXw/100x100"
              />
              <div class="bubble top bottom">Oui !</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Répondre" class="circular reply icon"></i
                ><span class="react"
                  ><i title="Aimer" class="circular heart outline icon"></i
                  ><i
                    title="Pouce en l'air"
                    class="circular thumbs up outline icon"
                  ></i
                  ><i title="Content" class="circular smile outline icon"></i
                  ><i
                    title="Pas content"
                    class="circular frown outline icon"
                  ></i
                ></span>
              </div>
            </div>
            <div class="time">01:36:38</div>
            <div class="message mine">
              <div class="bubble top bottom">Incroyable !</div>
              <div class="reacts"></div>
              <div class="controls">
                <i title="Supprimer" class="circular trash icon"></i
                ><i title="Editer" class="circular edit icon"></i
                ><i title="Répondre" class="circular reply icon"></i>
              </div>
            </div>
            <div class="view">
              <img
                title="Vu par Alice à 01:36:39"
                src="https://source.unsplash.com/mK_sjD0FrXw/100x100"
              /><img
                title="Vu par Gael à 01:36:39"
                src="https://source.unsplash.com/OYH7rc2a3LA/100x100"
              />
            </div>
          </div>
        </div>

        <div class="typing">
          <div class="wrapper">
            Alice est en train d'écrire...
          </div>
        </div>
        <div class="conversation-footer">
          <div class="wrapper">
            <p>
              <i title="Abandonner" class="circular times small icon link"></i>
              Répondre à Alice :
              <span>
                On peut même éditer ou supprimer des messages !
              </span>
            </p>

            <div class="ui fluid search">
              <div class="ui icon input">
                <input
                  class="prompt"
                  type="text"
                  placeholder="Rédiger un message"
                />
                <i class="send icon"></i>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="conversation-sidebar" v-if="groupPanel">
        <Group />
      </div>
    </div>
  </div>
</template>

<script>
import Group from "@/components/Group/Group";
import { mapActions, mapGetters } from "vuex";

export default {
  name: "Conversation",
  components: { Group },
  data() {
    return {
      groupPanel: false,
      nomConversation: ""
    };
  },
  mounted() {
    this.scrollBottom();
  },
  updated() {
    this.scrollBottom();
  },
  computed: {
    ...mapGetters(["conversation","users"])
  },
  methods: {
    ...mapActions([]),
    scrollBottom() {
      setTimeout(() => {
        let scrollElement = document.querySelector("#scroll");
        if (scrollElement) {
          scrollElement.scrollTop = document.querySelector(
            "#scroll"
          ).scrollHeight;
        }
      }, 0);
    },

    findPicture: function(c) {
      if(c.participants.length < 3)
        return this.users.find((element) => element.username===c.participants[1]).picture_url;
      else
        return "data:image/png;base64,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";
    },

  },
  watch: {
    // eslint-disable-next-line no-unused-vars
    conversation(newConversation, oldConversation) {
      this.scrollBottom();
    }
  }
};
</script>

<style src="./Conversation.css" scoped />
