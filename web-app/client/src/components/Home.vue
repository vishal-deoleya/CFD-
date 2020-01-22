<template>
  <div class="posts">
    <h1>2020 Presidential Election</h1>
    <!-- <h3>If you are a registered voter, enter your voterId below</h3> -->
    <!--span><b>{{ response }}</b></span><br /-->

    <div class="limiter">
      <div id="right">
      <div class="container-login100">
        <div class="wrap-login100">

          <form v-on:submit="validateVoter" class="login100-form validate-form">
          
            <span class="login100-form-title p-b-26">
                Enter Voter Id 
            </span>
            
            <div class="wrap-input100 validate-input" data-validate = "Valid email is: a@b.c">
              <input class="input100" type="text" v-model="loginData.voterId" name="voterId">
              <span class="focus-input100" data-placeholder="Voter Id"></span>
            </div>

            
            <div class="container-login100-form-btn">
              <div class="wrap-login100-form-btn">
                <div class="login100-form-bgbtn"></div>
                <button type="submit" class="login100-form-btn">
                  Login
                </button>
              </div>
            </div>


            <span v-if="loginReponse">
              <b>{{ loginReponse.data }}</b>
            </span>
            <br>
          </form>
        </div>
      </div>
    </div>

    <div id="vl"></div>

    <div id="left">

    <h3 style="
    font-size: 2.5em;
">Sign Up Now</h3>


    <div class="container-login100">
      <form v-on:submit="registerVoter">

        <div class="wrap-input100 validate-input">
          <input class="input100" type="text" v-model="registerData.voterId" >
          <span class="focus-input100" data-placeholder="Aadhar Number"></span>
        </div>

        <br>

        <div class="wrap-input100 validate-input">
          <input class="input100" type="text" v-model="registerData.registrarId" >
          <span class="focus-input100" data-placeholder="Registrar Id"></span>
        </div>

        <br>

        <div class="wrap-input100 validate-input">
          <input class="input100" type="text" v-model="registerData.firstName">
          <span class="focus-input100" data-placeholder="First Name"></span>
        </div>

        <br>

        <div class="wrap-input100 validate-input" >
          <input class="input100" type="text" v-model="registerData.lastName" >
          <span class="focus-input100" data-placeholder="Last Name"></span>
        </div>


        <!-- <input type="text" v-model="registerData.voterId" placeholder="Enter Aadhar Number"> -->
        
        <!-- <input type="text" v-model="registerData.registrarId" placeholder="Enter Registrar ID"> -->
        <!-- <br> -->
        <!-- <input type="text" v-model="registerData.firstName" placeholder="Enter first name"> -->
        <!-- <br> -->
        <!-- <input type="text" v-model="registerData.lastName" placeholder="Enter last name"> -->
        <!-- <br> -->

        <div class="container-login100-form-btn">
          <div class="wrap-login100-form-btn">
            <div class="login100-form-bgbtn"></div>
            <button type="submit" class="login100-form-btn" value="Register">
              Register
            </button>
          </div>
        </div>
      </form>
    </div>
    </div>
    <br>
    <span v-if="registerReponse">
      <b>{{ registerReponse.data }}</b>
    </span>
    <br>
    <vue-instant-loading-spinner id='loader' ref="Spinner"></vue-instant-loading-spinner>
    </div>
  </div>
</template>

<script>
import PostsService from "@/services/apiService";
import VueInstantLoadingSpinner from "vue-instant-loading-spinner/src/components/VueInstantLoadingSpinner.vue";

export default {
  name: "response",
  data() {
    return {
      loginData: {},
      registerData: {},
      registerReponse: {
        data: ""
      },
      loginReponse: {
        data: ""
      }
    };
  },
  components: {
    VueInstantLoadingSpinner
  },
  methods: {
    async registerVoter() {

      await this.runSpinner();
      const apiResponse = await PostsService.registerVoter(
        this.registerData.voterId,
        this.registerData.registrarId,
        this.registerData.firstName,
        this.registerData.lastName
      );

      console.log(apiResponse);
      this.registerReponse = apiResponse;
      await this.hideSpinner();
    },

    async validateVoter() {
      await this.runSpinner();

      if (!this.loginData.voterId) {
        console.log("!thislogin");
        let response = 'Please enter a VoterId';
        this.loginReponse.data = response;
        await this.hideSpinner();
      } else {
        const apiResponse = await PostsService.validateVoter(
          this.loginData.voterId
        );
        console.log("apiResponse");
        console.log(apiResponse.data);

        if (apiResponse.data.error) {
          // console.log(apiResponse);
          console.log(apiResponse.data.error);
          this.loginReponse = apiResponse.data.error;
        } else {
          this.$router.push("castBallot");
        }

        console.log(apiResponse);
        this.loginReponse = apiResponse;
        // this.$router.push('castBallot')
        await this.hideSpinner();
      }
    },
    async runSpinner() {
      this.$refs.Spinner.show();
    },
    async hideSpinner() {
      this.$refs.Spinner.hide();
    }
  }
};
</script>

