<template>
  <div style="margin: 2rem auto; width: 400px;">
    <div style="display: flex; margin-bottom: 2rem;">
      <div style="margin-right: 2rem;">
        <input
          class="form-control"
          type="text"
          placeholder="Name of practice or clinic"
          v-model="$v.clinic.name.$model"
        />
        <div
          class="error"
          v-if="!$v.clinic.name.required && $v.clinic.name.$anyDirty"
        >
          Name is required.
        </div>
      </div>
      <div >
        <input
          class="form-control"
          placeholder="Type of practice or clinic"
          v-model="$v.clinic.type_clinic.$model"
        />
        <div
          class="error"
          v-if="
            !$v.clinic.type_clinic.required && $v.clinic.type_clinic.$anyDirty
          "
        >
          Type of practice or clinic is required.
        </div>
      </div>
    </div>
    <div style="display: flex; margin-bottom: 2rem;">
      <div style="margin-right: 2rem;">
        <input
          class="form-control"
          type="email"
          placeholder="Email address"
          v-model="$v.clinic.email.$model"
        />
        <div
          class="error"
          v-if="!$v.clinic.email.required && $v.clinic.email.$anyDirty"
        >
          Email address is required.
        </div>
        <div
          class="error"
          v-if="!$v.clinic.email.email && $v.clinic.email.$anyDirty"
        >
          Email is invalid
        </div> 
      </div>
      <div >
        <input
          class="form-control"
          type="text"
          placeholder="Phone Number"
          v-model="$v.clinic.phone.$model"
        />
        <div
          class="error"
          v-if="!$v.clinic.phone.required && $v.clinic.phone.$anyDirty"
        >
          Phone number is required.
        </div>
      </div>
    </div>

    <div style="display: flex; margin-bottom: 2rem;">
      <div style="margin-right: 2rem;">
        <input
          class="form-control"
          type="text"
          placeholder="Website"
          v-model="$v.clinic.website.$model"
        />
        <div
          class="error"
          v-if="!$v.clinic.website.required && $v.clinic.website.$anyDirty"
        >
          Website is required.
        </div>
      </div>
      <div >
        <input
          class="form-control"
          type="number"
          placeholder="Years in Business"
          v-model="$v.clinic.year_in_business.$model"
        />
        <div
          class="error"
          v-if="
            !$v.clinic.year_in_business.required &&
              $v.clinic.year_in_business.$anyDirty
          "
        >
          Years in business is required.
        </div>
      </div>
    </div>

    <div style="display: flex; margin-bottom: 2rem;">
      <div style="margin-right: 2rem;">
        <input
          class="form-control"
          type="text"
          placeholder="Contact Person"
          v-model="$v.clinic.contact_person.$model"
        />
        <div
          class="error"
          v-if="
            !$v.clinic.contact_person.required &&
              $v.clinic.contact_person.$anyDirty
          "
        >
          Contact person is required.
        </div>
      </div>
      <div >
        <input
          class="form-control"
          type="text"
          placeholder="Title"
          v-model="$v.clinic.title.$model"
        />
        <div
          class="error"
          v-if="!$v.clinic.title.required && $v.clinic.title.$anyDirty"
        >
          Title is required.
        </div>
      </div>
    </div>

    <div class="row mb-40">
      <!-- <div class="col-sm-6">
        <multiselect
          v-model="selectedCountry"
          :options="countries"
          :searchable="true"
          :close-on-select="true"
          :show-labels="false"
          track-by="id"
          label="name"
          placeholder="Country"
        ></multiselect>
      </div> -->
      <!-- <div class="col-sm-6">
        <multiselect
          v-model="selectedCity"
          :searchable="true"
          :close-on-select="true"
          :show-labels="false"
          :loading="isLoading"
          track-by="short_name"
          label="name"
          @search-change="searchCity"
          :show-no-results="false"
          :clear-on-select="false"
          :internal-search="false"
          open-direction="bottom"
          :options="cities"
          placeholder="City"
        ></multiselect>
      </div> -->
    </div>

    <div class="row mb-40">
      <!-- <div class="col-sm-12">
        <div class="title-22">Languages Spoken</div>
        <div
          v-for="(language, idx) in languages"
          :key="idx"
          class="form-check form-check-inline"
        >
          <input
            v-model="clinic.language_spokens"
            class="form-check-input"
            type="checkbox"
            :id="'chk__' + idx"
            :value="language"
          />
          <label class="form-check-label" :for="'chk__' + idx">{{
            language
          }}</label>
        </div>
      </div> -->
    </div>

    <div class="row mt-20">
      <div class="col-sm-12">
        <button
          class="btn btn-danger btn-round pl-50 pr-50"
          :disabled="$v.$invalid"
          @click.prevent="onSendFeedback"
        >
          Submit
        </button>
        <span class="ml-3 text-primary title-16" v-if="isSubmited"
          >Message Sent</span
        >
      </div>
    </div>
  </div>
</template>

<script>
import { validationMixin } from "vuelidate";
import { required, email } from "vuelidate/lib/validators";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  mixins: [validationMixin],
  data() {
    return {
      clinic: {
        name: "",
        type_clinic: "",
        email: "",
        website: "",
        year_in_business: "",
        contact_person: "",
        phone: "",
        // country: "",
        title: "",
        // city: "",
        // language_spokens: [],
      },
      isSubmited: false
    }
  },
  validations: {
    clinic: {
      name: { required },
      type_clinic: { required },
      email: { required, email },
      website: { required },
      year_in_business: { required },
      contact_person: { required },
      phone: { required },
      // country: { required },
      title: { required },
      // city: { required },
      // language_spokens: { required },
    },
  },
  methods: {
    onSendFeedback(){
      console.log('onSendFeedback');
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input{
  height: 36px;
  width: 300px;
}
button{
  height: 36px;
  width: 70px;
}
.error {
  color: #ff00008c;
}

.error:focus {
  outline-color: #f99;
}
</style>
