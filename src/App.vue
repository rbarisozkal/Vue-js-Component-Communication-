<template>
  <section>
    <header><h1>My friends</h1></header>
    <new-friend @add-new="submitContact"></new-friend>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :id="friend.id"
        :key="friend.id"
        :name="friend.name"
        :is-favorite="friend.isFavorite"
        :phone-number="friend.number"
        :email-address="friend.emailAddress"
        @delete-friend="deleteFriend"
        >{{ friend }}</friend-contact
      >
    </ul>
   
  </section>
</template>

<script>
import FriendContact from "./components/FriendContact.vue";
export default {
  components: { FriendContact },
  data() {
    return {
      friends: [
        {
          id: "manuel",
          name: "baris",
          number: "123123",
          emailAddress: "asdfg",
        },
        { id: "selen", name: "selen", number: "3251", emailAddress: "abfjhwe" },
      ],
    };
  },
  methods:{
    submitContact(name,phone,email){
      const newFriendData={
        id:new Date().toISOString(),
        name:name,
        number:phone,
        emailAddress:email
      }
      this.friends.push(newFriendData);
    },
    deleteFriend(id){
            this.friends=this.friends.filter(friend=>friend.id!==id)
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li,#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>
