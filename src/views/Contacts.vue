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
      contacts: [
        {
          id: 1,
          firstName: 'Max',
          secondName: 'Mustermann',
          work: 'student',
          email: ' test22@gmail.com',
          phone: '018278739',
          gender: 'MALE'
        },
        {
          id: 2,
          firstName: 'Lisa',
          secondName: 'Müller',
          work: 'student',
          email: ' test32@gmail.com',
          phone: '84498',
          gender: 'FEMALE'
        }
      ]
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
  }
}
</script>
