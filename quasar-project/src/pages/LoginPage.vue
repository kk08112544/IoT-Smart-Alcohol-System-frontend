<template>
  <q-page>
    <q-img src="Building07-scaled.jpg" style="height: 100vh;">
      <div class="flex flex-center absolute-full text-subtitle2">
        <q-card class="my-card q-px-md p-py-md" style="background-color: rgba(255, 255, 255, 0.7);">
          <div class="flex flex-center">
            <q-icon name="account_circle" color="grey-6" size="4rem" />
          </div>
          <q-card-section>
            <q-form @submit.prevent="onSubmit" class="q-gutter-md">
              <div>
                <q-input v-model="username" type="text" label="Username"/>
              </div>
              <div>
                <q-input v-model="password" :type="isPwd ? 'password' : 'text'" label="Password">
                  <template v-slot:append>
                    <q-icon @click="togglePwdVisibility" :name="isPwd ? 'visibility_off' : 'visibility'"/>
                  </template>
                </q-input>
              </div>
              <div>
                <q-btn label="Login" no-caps type="submit" color="primary" style="width: 100%;" />
              </div>
              <div>
                <text-caption class="text-cyan-8">Not registered?
                  <router-link to="/register">Create an Account</router-link>
                </text-caption>
              </div>
            </q-form>
          </q-card-section>
        </q-card>
      </div>
    </q-img>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "LoginPage",
  data() {
    return {
      username: null,
      password: null,
      isPwd: false,
    };
  },
  methods: {
    async onSubmit() {
      try {
        const response = await this.$axios.post(`https://deploy-api-psi.vercel.app/api/auth/login`, {
          username: this.username,
          password: this.password,
        });

        const accessToken = response.data.accessToken;
        const roleId = response.data.role_id;
        const userId = response.data.id;
        const name = response.data.name;
        const lastname = response.data.lastname;

        localStorage.setItem("roleId", roleId);
        localStorage.setItem("accessToken", accessToken);
        localStorage.setItem("userId", userId);
        localStorage.setItem("name", name);
        localStorage.setItem("lastname", lastname);

        this.$q.notify({
          color: "green-4",
          textColor: "white",
          type: "positive",
          message: "Logged in successfully",
        });

        this.$router.push(parseInt(roleId, 10) === 1 ? "/director/dashboard" : "/user/alcohol");
      } catch (error) {
        console.log("Login error", error);
        this.$q.notify({
          color: "negative",
          textColor: "white",
          type: "negative",
          message: "Invalid username or password",
        });
      }
    },
    togglePwdVisibility() {
      this.isPwd = !this.isPwd;
    },
  },
});
</script>
