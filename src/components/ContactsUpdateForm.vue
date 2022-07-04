<template>

  <div class="offcanvas offcanvas-end"   style="left:0"  tabindex="1" id="contacts-update-offcanvas" aria-labelledby="offcanvas-label">
    <div class="offcanvas-header">
      <h5 id="offcanvas-label">Edit Contact</h5>
      <button type="button" id="close-offcanvas" class="btn-close text-reset" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body" >
  <form class="text-start needs-validation" id="contacts-update-form" novalidate>
    <div class="mb-3">
      <label for="first-name" class="form-label">First Name</label>
      <input type="text" class="form-control"  id="first-name" v-model="firstName" required>
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
      <button class="btn btn-primary me-3" type="edit" @click.prevent="editContact">Edit</button>
      <button class="btn btn-danger" type="reset">Reset</button>
    </div>
  </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactsUpdateForm'
}
</script>
<style scoped>
.ticky-button {
  position: fixed;
  bottom: 100px;
  left: 20px;
  padding: 10px 15px;
  border-radius: 30px;
}
</style>
