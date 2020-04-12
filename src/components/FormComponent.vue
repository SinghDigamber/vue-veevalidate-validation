<template>
<ValidationObserver ref="observer">
    <b-form slot-scope="{ validate }" @submit.prevent="validate().then(handleSubmit)">
      <ValidationProvider rules="required" name="Name">
        <b-form-group slot-scope="{ valid, errors }" label="Name">
            <b-form-input
              type="text"
              v-model="user.name"
              :state="errors[0] ? false : (valid ? true : null)"
              placeholder="Enter name">
            </b-form-input>
            <b-form-invalid-feedback>
              {{ errors[0] }}
            </b-form-invalid-feedback>
        </b-form-group>
      </ValidationProvider>

      <ValidationProvider rules="required|email" name="Email">
        <b-form-group 
          slot-scope="{ valid, errors }"
          label="Email">
            <b-form-input
              type="email"
              v-model="user.email"
              :state="errors[0] ? false : (valid ? true : null)"
              placeholder="Enter email">
            </b-form-input>
            <b-form-invalid-feedback>
              {{ errors[0] }}
            </b-form-invalid-feedback>
        </b-form-group>
      </ValidationProvider>

      <ValidationProvider rules="required" name="Mobile">
        <b-form-group 
          slot-scope="{ valid, errors }"
          label="Mobile">
            <b-form-input
              type="text"
              v-model="user.mobile"
              :state="errors[0] ? false : (valid ? true : null)"
              placeholder="Enter mobile no">
            </b-form-input>
            <b-form-invalid-feedback>
              {{ errors[0] }}
            </b-form-invalid-feedback>
        </b-form-group>
      </ValidationProvider>

      <ValidationProvider name="City" rules="required">
        <b-form-group slot-scope="{ valid, errors }" label="City:">
          <b-form-select 
            :state="errors[0] ? false : (valid ? true : null)" 
            v-model="user.city">
            <option value="">Choose</option>
            <option value="CA">Los Angeles</option>
            <option value="IL">Chicago</option>
            <option value="LA">New Orleans</option>
            <option value="NM">Santa Fe</option>
          </b-form-select>
            <b-form-invalid-feedback>
              {{ errors[0] }}
            </b-form-invalid-feedback>
        </b-form-group>
      </ValidationProvider>

      <ValidationProvider rules="required" name="Password" vid="password">
        <b-form-group 
          slot-scope="{ valid, errors }"
          label="Password">      
            <b-form-input
              type="password"
              v-model="user.password"
              :state="errors[0] ? false : (valid ? true : null)"
              placeholder="Enter password">
            </b-form-input>
            <b-form-invalid-feedback>
              {{ errors[0] }}
            </b-form-invalid-feedback>
        </b-form-group>
      </ValidationProvider>

      <ValidationProvider rules="required|confirmed:password" name="Confirm Password">
        <b-form-group 
          slot-scope="{ valid, errors }"
          label="Confirm Password">
            <b-form-input
              type="password"
              v-model="user.confirmation"
              :state="errors[0] ? false : (valid ? true : null)">
            </b-form-input>
            <b-form-invalid-feedback>
              {{ errors[0] }}
            </b-form-invalid-feedback>
        </b-form-group>
      </ValidationProvider>

      <ValidationProvider name="Hobbies" rules="required|length:1">
        <b-form-group slot-scope="{ valid, errors }">
          <b-form-checkbox-group 
            :state="errors[0] ? false : (valid ? true : null)" 
            v-model="user.hobbies">
            <b-form-checkbox value="Reading">Reading</b-form-checkbox>
            <b-form-checkbox value="Gyming">Gyming</b-form-checkbox>
            <b-form-checkbox value="Movies">Movies</b-form-checkbox>
          </b-form-checkbox-group>
          <b-form-invalid-feedback>
            {{ errors[0] }}
          </b-form-invalid-feedback>
        </b-form-group>
      </ValidationProvider>

      <b-button block type="submit" variant="primary">Submit</b-button>
    </b-form>
</ValidationObserver>
</template>

<script>
import { ValidationObserver, ValidationProvider } from 'vee-validate';

export default {
  components: {
    ValidationObserver,
    ValidationProvider
  },
  data: () => ({
    user:{
        name: '',
        email: '',
        mobile: '',
        city: '',
        password: '',
        confirmation: '',
        hobbies: []
    }
  }),
  methods: {
    handleSubmit () {
      console.log(this.user);
    }
  }
};
</script>

<style lang="scss">
form {
   max-width: 500px;
   margin: 0 auto; 
   text-align: left;
}
.form-group > label {
    font-weight: 600;
}
</style>