<template>
    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div v-if="this.message" >
            {{ message }}
      </div>
      <div  v-for="contact in contacts" :key="contact.id">
        <section>
          <div class="card-container">
            <img src="https://www.alliancecoatingsystems.com/wp-content/uploads/2016/05/contact-background-1.jpg" alt="">

            <div class="profile-container">
              <img :src="getAvatar(contact)" :alt="contact.firstName + ' ' + contact.secondName">
            </div>

            <span class="profile-info">
      <span>
         <p class="name">{{contact.firstName}} {{contact.secondName}}</p>

      </span>
      <p class="work">{{contact.work}}</p>
    </span>
            <div class="number-data">
    <span>
      <p>{{contact.email}}</p>
      <p><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="blue" class="bi bi-envelope-fill" viewBox="0 0 16 16">
  <path d="M.05 3.555A2 2 0 0 1 2 2h12a2 2 0 0 1 1.95 1.555L8 8.414.05 3.555ZM0 4.697v7.104l5.803-3.558L0 4.697ZM6.761 8.83l-6.57 4.027A2 2 0 0 0 2 14h12a2 2 0 0 0 1.808-1.144l-6.57-4.027L8 9.586l-1.239-.757Zm3.436-.586L16 11.801V4.697l-5.803 3.546Z"/>
</svg> </p>
    </span>
              <span>
      <p> {{contact.phone}}</p>
      <p><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="blue" class="bi bi-telephone" viewBox="0 0 16 16">
  <path d="M3.654 1.328a.678.678 0 0 0-1.015-.063L1.605 2.3c-.483.484-.661 1.169-.45 1.77a17.568 17.568 0 0 0 4.168 6.608 17.569 17.569 0 0 0 6.608 4.168c.601.211 1.286.033 1.77-.45l1.034-1.034a.678.678 0 0 0-.063-1.015l-2.307-1.794a.678.678 0 0 0-.58-.122l-2.19.547a1.745 1.745 0 0 1-1.657-.459L5.482 8.062a1.745 1.745 0 0 1-.46-1.657l.548-2.19a.678.678 0 0 0-.122-.58L3.654 1.328zM1.884.511a1.745 1.745 0 0 1 2.612.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z"/>
</svg></p>
    </span>
           </div>
      <div class="number-data buttons">

             <button class="edit"  @click="showContact(contact.id)" data-bs-toggle="offcanvas" data-bs-target="#contacts-update-offcanvas" aria-controls="#contacts-update-offcanvas"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-pencil" viewBox="0 0 16 16">
  <path d="M12.146.146a.5.5 0 0 1 .708 0l3 3a.5.5 0 0 1 0 .708l-10 10a.5.5 0 0 1-.168.11l-5 2a.5.5 0 0 1-.65-.65l2-5a.5.5 0 0 1 .11-.168l10-10zM11.207 2.5 13.5 4.793 14.793 3.5 12.5 1.207 11.207 2.5zm1.586 3L10.5 3.207 4 9.707V10h.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.5h.293l6.5-6.5zm-9.761 5.175-.106.106-1.528 3.821 3.821-1.528.106-.106A.5.5 0 0 1 5 12.5V12h-.5a.5.5 0 0 1-.5-.5V11h-.5a.5.5 0 0 1-.468-.325z"/>
</svg>
 Edit </button>

        <button class="delete"   @click="deletecontact(contact.id)"  >
                  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16">
  <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
  <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
</svg>
                  Delete</button>
           </div>
          </div>
        </section>
    </div>
    </div>
</template>

<script>
export default {
  name: 'ContactCardList',
  props: {
    contacts: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      contbyid: [],
      message: null
    }
  },
  methods: {
    getAvatar (contact) {
      if (contact.gender === 'MALE') {
        return require('../assets/MALE.png')
      } else if (contact.gender === 'FEMALE') {
        return require('../assets/FEMALE.png')
      }
    },
    async deletecontact (contact) {
      const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/contacts/' + contact
      const headers = new Headers()
      headers.append('Content-Type', 'application/json')

      const requestOptions = {
        method: 'DELETE',
        headers: headers,
        body: contact,
        redirect: 'follow'
      }

      let response = await fetch(endpoint, requestOptions)
      if (response.ok) {
        this.message = 'Deleted'
        this.contacts.filter(element => element !== contact)
        await this.$router.push('/')
      } else if (response.status === 400) {
        response = await response.json()
      } else {
        this.message = 'Unknown error occurred'
      }
    },
    async showContact (contact) {
      const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/contacts/' + contact
      const headers = new Headers()
      headers.append('Content-Type', 'application/json')
      headers.append('Content-Type', 'application/json')

      const requestOptions = {
        method: 'GET',
        headers: headers,
        body: contact,
        redirect: 'follow'
      }
      const response = await fetch(endpoint, requestOptions)
      for (const e in response) {
        this.contbyid.push(e)
      }
    }
  }
}
</script>

<style scoped>
:root {
  --color-normal-text: white;
  --background-card-color: white;
  --color-bold-text: white;
  --background-color: #2e2e2e;
}

body {
  background-color: var(--background-color);
  font-family: 'Barlow', sans-serif;
}
section {
  display: flex;
  justify-content: center;
  align-items: center;
}
.card-container {
  background: rgb(238,174,202);
  background:  linear-gradient(315deg, #339cec 0%, #0a0e2b 100%);

  width: 350px;
  border-radius: 10px;
  text-align: center;
  margin-top: 30px;
}
.card-container img {
  width: 100%;
  object-fit: cover;
  height: 110px;
  border-radius: 10px 10px 0px 0px;
  margin-bottom: 30px;
  background: transparent;
}
.profile-container {
  background-color: var(--background-card-color);
  width: 80px;
  height: 80px;
  border-radius: 50%;
  padding: 5px;
  margin: 0 auto;
  /*    */
position:relative;
  top: 100%;
  right: 0;
  left: 0;
}
.profile-container img {
  width: 100%;
  object-fit: cover;
  height: auto;
position: absolute;
  border-radius: 50%;
 top: -100%;
}
.profile-info span:nth-child(1) {
  display: flex;
  justify-content: center;
}
.profile-info span:nth-child(1) p:nth-child(1) {
  margin-right: 10px;
}

.number-data {
  display: flex;
  justify-content: space-around;
}

.profile-info .name{
  color: white;
  font-weight: 700;
  font-size: 30px ;
}

.number-data span p:nth-child(1) {
  margin-bottom: 5px;
  font-weight: bold;
  color: white;
  font-size: 16px;
}

.number-data span p:nth-child(2) {
  margin-top: 0px;
  font-size: 16px;
  color: white;
}

.card-container hr {
  border-bottom: none;
  border-top-color: white;
}

.profile-info .city {
  margin-top: 0px;
  color: white;
  font-size: 16px ;
}
.buttons {
 width:100%;
  margin-bottom: 5px;
  display: flex;
  justify-content: space-between;
align-content: center;
  padding-right: 20%;
  padding-left: 20%;
}
.buttons button {
  color: black;
  font-weight: 500;
  font-size: 20px;
}
.delete {
  background: lightcoral;
}
.edit {
  background: lightyellow;
}
</style>
