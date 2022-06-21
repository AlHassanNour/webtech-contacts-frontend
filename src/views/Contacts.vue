<template>
  <h1> Welcome to Contacts</h1>
  <div class="container-fluid" >
<div class="row row-cols-1 row-cols-md-3 g-4">
<div class="col" v-for="contact in contacts" :key="contact.id">
  <div class="card h-100">
    <img :src="getAvatar(contact)" class="card-img-top" :alt="contact.firstName + ' ' + contact.secondName">
    <div class="card-body">
      <h5 class="card-title">{{contact.firstName}} {{contact.secondName}}</h5>
      <p class="card-text">Work : {{contact.work}}</p>
      <p class="card-text">E-Mail : {{contact.email}}</p>
      <p class="card-text">Phone : {{contact.phone}}</p>
</div>
  </div>
</div>
</div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: 'Contacts',
  data () {
    return {
      contacts: []
    }
  },
  methods: {
    getAvatar (contact) {
      if (contact.gender === 'MALE') {
        return require('../assets/MALE.png')
      } else if (contact.gender === 'FEMALE') {
        return require('../assets/FEMALE.png')
      }
    }
  },
  mounted () {
    const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/contacts'
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }

    fetch(endpoint, requestOptions)
      .then(response => response.json())
      .then(result => result.forEach(contact => {
        this.contacts.push(contact)
      }))
      .catch(error => console.log('error', error))
  }
}
</script>
<style scoped>
.main {
  padding: 50px;
  min-height: 100px;
  width:100%;
  overflow: hidden;
  background-color: #fff;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  align-items: center;
  border-radius: 5px;
}
.card {
  padding: 10px;
  margin: 10px;
  border: #000 2px solid;
}
.card-img-top {
  flex: 0.3;
  height: 100px;
  width: 100%;

  padding: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-right: 1px solid #f2f0f1;
}
.card-img-top {
  width: 100px ;
  border-radius: 50%;
}
.contact {
  flex: 0.7;
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 20px;
}
.contact > * {
  margin: 0;
}

.card-title {
  margin-bottom: 15px;
}

.contact__btn {
  background-color: #398a13;
  border: none;
  outline: none;
  width: 150px;
  padding: 10px;
  color: #fff;
  margin-bottom: 10px;
}
.delete__btn {
  background-color: #c81811;
  border: none;
  outline: none;
  width: 150px;
  padding: 10px;
  color: #fff;
}
</style>
