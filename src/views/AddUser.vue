<template>
  <div class="row clearfix main">
    <div class="col-md-12">
      <div
        v-if="submitted"
        class="alert alert-success alert-dismissible fade show"
        role="alert"
      >
        Hurray!!! You have created a new user.
        <button
          type="button"
          class="close"
          data-dismiss="alert"
          aria-label="Close"
        >
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="card">
        <div class="header">
          <h2>Add User</h2>
        </div>
        <div class="body">
          <form
            id="basic-form"
            autocomplete="off"
            novalidate
            @submit.prevent="validateForm"
          >
            <div class="form-group">
              <label>Name</label>
              <input
                type="text"
                class="form-control"
                @input="touchInput('name')"
                v-model="form.name"
              />
              <small
                v-if="$v.form.name.$dirty && !$v.form.name.required"
                class="form-text text-danger"
                >Name is required</small
              >
            </div>
            <div class="form-group">
              <label>Email</label>
              <input
                type="email"
                class="form-control"
                @input="touchInput('email')"
                v-model="form.email"
              />
              <small
                v-if="$v.form.email.$dirty && !$v.form.email.required"
                class="form-text text-danger"
                >Email is required</small
              >
              <small
                v-if="$v.form.email.$dirty && !$v.form.email.email"
                class="form-text text-danger"
                >Email is not valid</small
              >
            </div>
            <div class="form-group">
              <label>Description</label>
              <textarea
                class="form-control"
                rows="5"
                cols="30"
                @input="touchInput('description')"
                v-model="form.description"
              ></textarea>
              <small
                v-if="
                  $v.form.description.$dirty && !$v.form.description.required
                "
                class="form-text text-danger"
                >Description is required</small
              >
              <small
                v-if="
                  $v.form.description.$dirty && !$v.form.description.minLength
                "
                class="form-text text-danger"
                >Description should have a minimum of 200 characters</small
              >
            </div>
            <div class="form-group">
              <label>Gender</label>
              <br />
              <label class="fancy-radio">
                <input
                  type="radio"
                  name="gender"
                  value="male"
                  @input="touchInput('gender')"
                  v-model="form.gender"
                />
                <span><i></i>Male</span>
              </label>
              <label class="fancy-radio">
                <input
                  type="radio"
                  name="gender"
                  value="female"
                  @input="touchInput('gender')"
                  v-model="form.gender"
                />
                <span><i></i>Female</span>
              </label>
              <small
                v-if="$v.form.gender.$dirty && !$v.form.gender.required"
                class="form-text text-danger"
                >Gender is required</small
              >
            </div>
            <br />
            <button type="submit" class="btn btn-primary">Add User</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { validationMixin } from 'vuelidate';
import { required, email, minLength } from 'vuelidate/lib/validators';

export default {
  mixins: [validationMixin],
  data: () => ({
    form: {
      name: null,
      email: null,
      description: null,
      gender: null
    },
    submitted: false
  }),
  validations: {
    form: {
      name: {
        required
      },
      email: {
        required,
        email
      },
      description: {
        required,
        minLength: minLength(200)
      },
      gender: {
        required
      }
    }
  },
  methods: {
    validateForm() {
      this.$v.$touch();

      if (!this.$v.$invalid) {
        this.submitForm(this.form);
      }
    },
    touchInput(inputName) {
      this.$v.form[inputName].$touch();
    },
    submitForm(form) {
      console.log(form);
      this.submitted = true;
    }
  }
};
</script>

<style lang="scss">
.main {
  padding-top: 25px;
}
</style>
