<template>
  <div id="contact">
    <div id="contact-form">
      <form @submit.prevent="onSubmit">
        <div v-if="sent" id="success" class="zoomInDown animated">
          Your message has been sent
          <span style="font-size:10px;">&#128512;</span>.
        </div>
        <div v-if="notsent" id="error" class="rubberBand animated">
          Oops <span style="font-size:10px;">&#128556;</span> Something went
          wrong.
        </div>
        <div id="contact-header">
          <p class=" fadeInUp animated">Contact me</p>
        </div>

        <div
          class="input fadeInUp animated"
          :class="{ invalidInput: $v.name.$error }"
        >
          <input
            class="form__input"
            type="text"
            id="name"
            placeholder="Your Name..."
            @blur="$v.name.$touch()"
            v-model="name"
          />
        </div>

        <div
          class="input fadeInUp animated"
          :class="{ invalidInput: $v.email.$error }"
        >
          <input
            type="email"
            id="email"
            placeholder="Your email..."
            @blur="$v.email.$touch()"
            v-model="email"
          />
          <p v-if="!$v.email.email">
            Please provide a valid email address.
          </p>
        </div>

        <div
          class="input fadeInUp animated"
          :class="{ invalidTextarea: $v.name.$error }"
        >
          <textarea
            id="msg"
            placeholder="Your message..."
            rows="3"
            @blur="$v.msg.$touch()"
            v-model="msg"
          ></textarea>
        </div>
        <div class="submit fadeInUp animated">
          <button :disabled="$v.$invalid" type="submit">
            <pulse-loader :loading="loading"></pulse-loader>Send
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import { required, email } from "vuelidate/lib/validators";
import PulseLoader from "vue-spinner/src/PulseLoader.vue";
import firebase from "firebase/app";
import "firebase/database";

var firebaseConfig = {
  apiKey: "AIzaSyAGoSrA-OosaVrIlQAN7ItF8it_C1EAQhM",
  authDomain: "portfoliomessages-8fd79.firebaseapp.com",
  databaseURL: "https://portfoliomessages-8fd79.firebaseio.com",
  projectId: "portfoliomessages-8fd79",
  storageBucket: "portfoliomessages-8fd79.appspot.com",
  messagingSenderId: "691966293120",
  appId: "1:691966293120:web:423aee76e07e78a352e265",
};
var app = firebase.initializeApp(firebaseConfig);
var db = app.database();
var messagesRef = db.ref("messages");

export default {
  components: {
    PulseLoader,
  },
  firebase: {
    messages: messagesRef,
  },
  data() {
    return {
      name: "",
      email: "",
      msg: "",
      sent: false,
      notsent: false,
      loading: false,
    };
  },
  validations: {
    name: { required },
    email: { required, email },
    msg: { required },
  },
  methods: {
    onSubmit() {
      //show  spinner
      this.loading = true;
      const formData = {
        name: this.name,
        email: this.email,
        msg: this.msg,
      };
      let task = messagesRef.push(formData);
      task.then(() => {
        //hide spinner
        this.loading = false;
        this.sent = true;
        this.name = "";
        this.msg = "";
        this.email = "";
        setTimeout(() => {
          this.sent = false;
        }, 3000);
      });
      task.catch(() => {
        this.notsent = true;
        setTimeout(() => {
          this.notsent = false;
        }, 3000);
      });
    },
  },
};
</script>

<style scoped>
#success {
  text-align: center;
  padding: 10px;
  background-color: rgb(71, 219, 71);
  color: white;
  margin-bottom: 10px;
}
#error {
  text-align: center;
  padding: 10px;
  background-color: rgb(224, 44, 44);
  color: white;
  margin-bottom: 10px;
}
#contact {
  height: 90vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  font-family: comfortaa;
  color: white;
}
#contact-form {
  margin: 0 auto;
  min-width: 320px;
}
#contact-header {
  text-align: center;
  font-size: 20px;
}

.input {
  margin: 40px auto;
}

.input input {
  font: inherit;
  width: 100%;
  padding: 6px 12px;
  background-color: transparent;
  border-color: transparent;
  border-bottom-color: #2f2f2f;
}
.input textarea {
  font: inherit;
  width: 100%;
  padding: 6px 12px;
  background-color: transparent;
  border: solid 2px #2f2f2f;
}

.input p {
  font-size: 10px;
  color: #ff4d5a;
  margin-top: 8px;
}

.input.inline input {
  width: auto;
}

.input input:focus {
  outline: none;
  border-bottom-color: white;
  color: white;
}
.input textarea:focus {
  outline: none;
  border-color: white;
  color: white;
}

.invalidInput {
  border-bottom-color: #ff4d5a;
  color: #ff4d5a;
}
.invalidTextarea {
  border-color: #ff4d5a;
  color: #ff4d5a;
}

.submit button {
  background-color: transparent;
  border: 1px solid white;
  border-radius: 100px;
  color: white;
  padding: 5px 10px;
  font: inherit;
  cursor: pointer;
  width: 100%;
  font-size: 12px;
}

.submit button:hover,
.submit button:active {
  background-color: white;
  color: black;
  outline: none;
}
.submit button:focus {
  outline: none;
}

.submit button[disabled],
.submit button[disabled]:hover,
.submit button[disabled]:active {
  background-color: transparent;
  color: #ff4d5a;
  cursor: not-allowed;
  outline: none;
}
</style>
