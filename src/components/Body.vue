<template>
  <div class="shadow p-3 mb-5 bg-white rounded">
    <ValidationObserver ref="observer" v-slot="{ handleSubmit }">
      <form
        v-if="currentPage === 1"
        @submit.prevent="handleSubmit(nextProcess)"
      >
        <ValidationProvider
          v-slot="{ errors, classes }"
          rules="required"
          name="name"
        >
          <div class="form-group">
            <label class="text-left d-flex">Full name</label>
            <input type="text" class="form-control" v-model="name" />
            <span :class="classes" class="styleSpan">{{ errors[0] }}</span>
          </div>
        </ValidationProvider>
        <ValidationProvider
          v-slot="{ errors, classes }"
          rules="required|email"
          name="email"
        >
          <div class="form-group">
            <label class="text-left d-flex">your email</label>
            <input type="text" class="form-control" v-model="email" />
            <span :class="classes" class="styleSpan">{{ errors[0] }}</span>
          </div>
        </ValidationProvider>
        <button
          class="btn btn-info"
          type="button"
          v-if="currentPage < totalPage"
          @click="prevProcess"
        >
          PREVIOUS
        </button>
        <button
          class="btn btn-primary ml-2"
          type="submit"
          v-if="currentPage < totalPage"
        >
          NEXT
        </button>
        <button
          class="btn btn-danger ml-2"
          type="button"
          @click="reset"
          v-if="currentPage === totalPage"
        >
          RESET
        </button>
      </form>
    </ValidationObserver>
    <ValidationObserver ref="observer" v-slot="{ handleSubmit }">
      <form
        v-if="currentPage === 2"
        @submit.prevent="handleSubmit(nextProcess)"
      >
        <ValidationProvider
          v-slot="{ errors, classes }"
          rules="required"
          name="companyname"
        >
          <div class="form-group">
            <label class="text-left d-flex">Company name</label>
            <input type="text" class="form-control" v-model="companyname" />
            <span :class="classes" class="styleSpan">{{ errors[0] }}</span>
          </div>
        </ValidationProvider>
        <ValidationProvider
          v-slot="{ errors, classes }"
          rules="required|numeric"
          name="numberofemployee"
        >
          <div class="form-group ">
            <label class="text-left d-flex">number of employee</label>
            <input
              type="text"
              class="form-control"
              v-model="numberofemployee"
            />
            <span :class="classes" class="styleSpan">{{ errors[0] }}</span>
          </div>
        </ValidationProvider>
        <button
          class="btn btn-info"
          type="button"
          v-if="currentPage < totalPage"
          @click="prevProcess"
        >
          PREVIOUS
        </button>
        <button
          class="btn btn-primary ml-2"
          type="submit"
          v-if="currentPage < totalPage"
        >
          NEXT
        </button>
        <button
          class="btn btn-danger ml-2"
          type="button"
          @click="reset"
          v-if="currentPage === totalPage"
        >
          RESET
        </button>
      </form>
    </ValidationObserver>
    <ValidationObserver ref="observer" v-slot="{ handleSubmit }">
      <form
        v-if="currentPage === 3"
        @submit.prevent="handleSubmit(finishProcess)"
      >
        <ValidationProvider
          v-slot="{ errors, classes }"
          rules="required"
          name="select"
        >
          <div class="input-group mb-3">
            <label>Form Where did you hear about us</label>
            <select
              class="custom-select"
              id="inputGroupSelect01"
              v-model="select"
            >
              <option selected>Choose...</option>
              <option value="friend">Friend</option>
              <option value="facebook">Facebook</option>
              <option value="google">Google</option>
            </select>
            <span :class="classes" class="styleSpan">{{ errors[0] }}</span>
          </div>
        </ValidationProvider>
        <ValidationProvider
          v-slot="{ errors, classes }"
          :rules="{ required: { allowFalse: false } }"
          name="checkbox"
        >
          <div class="form-group form-check d-flex">
            <input
              type="checkbox"
              v-model="checkbox"
              class="form-check-input"
              id="exampleCheck1"
            />
            <label class="form-check-label" for="exampleCheck1"
              >Check me out</label
            >
          </div>
          <span :class="classes" class="styleSpan">{{ errors[0] }}</span>
        </ValidationProvider>
        <button
          class="btn btn-info"
          type="button"
          v-if="currentPage < totalPage"
          @click="prevProcess"
        >
          PREVIOUS
        </button>
        <button class="btn btn-success" type="submit" v-if="currentPage === 3">
          Finish
        </button>
        <button
          class="btn btn-danger ml-2"
          type="button"
          @click="reset"
          v-if="currentPage === totalPage"
        >
          RESET
        </button>
      </form>
    </ValidationObserver>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      companyname: "",
      numberofemployee: "",
      select: "",
      checkbox: false,
    };
  },
  props: {
    currentPage: Number,
    checkValidate: Function,
    prevProcess: {
      type: Function,
      default: () => {
        return [];
      },
    },
    nextProcess: {
      type: Function,
      default: () => {
        return [];
      },
    },
    resetProcess: {
      type: Function,
      default: () => {
        return [];
      },
    },
    finishProcess: {
      type: Function,
      default: () => {
        return [];
      },
    },
    totalPage: {
      type: Number,
      default: () => {
        return "";
      },
    },
  },
  methods: {
    reset() {
      this.resetProcess();
      this.email = "";
      this.numberofemployee = "";
      this.select = "";
      this.checkbox = false;
      this.checkbox = true;
      this.checkbox = false;
      this.numberofemployee = "sadasdasdasdas";
    },
  },
};
</script>

<style scoped>
.styleSpan {
  color: red;
  padding: 5px;
  margin-top: 5px;
  text-align: left;
}
</style>
