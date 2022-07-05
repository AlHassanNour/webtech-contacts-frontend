<template>
  <button class="btn btn-success sticky-button" data-bs-toggle="offcanvas" data-bs-target="#contacts-create-offcanvas" aria-controls="#contacts-create-offcanvas">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-person-plus-fill" viewBox="0 0 16 16">
      <path d="M1 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1H1zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"/>
      <path fill-rule="evenodd" d="M13.5 5a.5.5 0 0 1 .5.5V7h1.5a.5.5 0 0 1 0 1H14v1.5a.5.5 0 0 1-1 0V8h-1.5a.5.5 0 0 1 0-1H13V5.5a.5.5 0 0 1 .5-.5z"/>
    </svg>
  </button>
  <div class="offcanvas offcanvas-end" tabindex="1" id="contacts-create-offcanvas" aria-labelledby="offcanvas-label">
    <div class="offcanvas-header">
      <h5 id="offcanvas-label">New Contact</h5>
      <button type="button" id="close-offcanvas" class="btn-close text-reset" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body">
  <form class="text-start needs-validation" id="contacts-create-form" novalidate>
    <div class="mb-3">
      <label for="first-name" class="form-label">First Name</label>
      <input type="text" class="form-control" id="first-name" v-model="firstName" required>
      <div class="invalid-feedback">
        Please provide the first name.
      </div>
    </div>
    <div class="mb-3">
      <label for="second-name" class="form-label">Second Name</label>
      <input type="text" class="form-control" id="second-name" v-model="secondName" required>
      <div class="invalid-feedback">
        Please provide the second name.
      </div>
    </div>
      <div class="mb-3">
        <label for="phone" class="form-label">Phone</label>
        <input type="text" class="form-control" id="phone" v-model="phone" required>
        <div class="invalid-feedback">
          Please provide the phone.
        </div>
      </div>
      <div class="mb-3">
        <label for="work" class="form-label"> Work</label>
        <input type="text" class="form-control" id="work" v-model="work">
      </div>
    <div class="mb-3">
      <label for="email" class="form-label"> E-Mail</label>
      <input type="email" class="form-control" id="email" v-model="email">
    </div>
    <div class="mb-3">
      <label for="gender" class="form-label">Gender</label>
      <select id="gender" class="form-select" v-model="gender" required>
        <option value="" selected disabled>Choose...</option>
        <option value="MALE">Male</option>
        <option value="FEMALE">Female</option>
        <option value="DIVERSE">Diverse</option>
      </select>
      <div class="invalid-feedback">
        Please select a valid gender.
      </div>
    </div>
    <div v-if="this.serverValidationMessages">
      <ul>
        <li v-for="(message,index) in serverValidationMessages" :key="index" style="color: #ff0000">
          {{ message }}
        </li>
      </ul>
    </div>
    <div class="mt-5">
      <button class="btn btn-primary me-3" type="submit" @click="createContact">Create</button>
      <button class="btn btn-danger" type="reset">Reset</button>
    </div>
  </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactsCreateForm',
  data () {
    return {
      firstName: '',
      secondName: '',
      gender: '',
      email: '',
      work: '',
      phone: '',
      serverValidationMessages: []
    }
  },
  emits: ['created'],
  methods: {
    async createContact () {
      if (this.validate()) {
        const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/contacts'
        const headers = new Headers()
        headers.append('Content-Type', 'application/json')

        const contact = JSON.stringify({
          firstName: this.firstName,
          secondName: this.secondName,
          gender: this.gender,
          email: this.email,
          work: this.work,
          phone: this.phone
        })
        const requestOptions = {
          method: 'POST',
          headers: headers,
          body: contact,
          redirect: 'follow'
        }
        const response = await fetch(endpoint, requestOptions)
        await this.handleResponse(response)
      }
    },
    async handleResponse (response) {
      if (response.ok) {
        this.$emit('created', response.headers.get('location'))
        document.getElementById('close-offcanvas').click()
      } else if (response.status === 400) {
        response = await response.json()
        response.errors.forEach(error => {
          this.serverValidationMessages.push(error.defaultMessage)
        })
      } else {
        this.serverValidationMessages.push('Unknown error occurred')
      }
    },

    validate () {
      const form = document.getElementById('contacts-create-form')
      form.classList.add('was-validated')
      return form.checkValidity()
    }
  }
}
</script>

<style scoped>
.sticky-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 10px 15px;
  border-radius: 30px;
}
</style>
