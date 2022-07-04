<template>
  <h1> Welcome to Contacts</h1>
  <div class="container-fluid" >
    <contact-card-list :contacts="this.contacts"></contact-card-list>
  </div>
  <ContactsCreateForm></ContactsCreateForm>
  <contacts-update-form></contacts-update-form>
</template>

<script>
import ContactCardList from '@/components/ContactCardList'
import ContactsCreateForm from '@/components/ContactsCreateForm'
import ContactsUpdateForm from '@/components/ContactsUpdateForm'
export default {
  // eslint-disable-next-line
  name: 'Contacts',
  components: {
    ContactsUpdateForm,
    ContactCardList,
    ContactsCreateForm
  },
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
