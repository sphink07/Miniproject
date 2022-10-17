<template>
  <div>
    <v-app>
      <v-container style="text-align: center">
        <h1 style="color: gold; font-size: 50px">Find Truth Value</h1>
        <span style="color: aliceblue; font-size: 20px">
          ──── Make by Nattanon ────
        </span>
        <v-row class="mt-5">
          <v-col cols="4">
            <h1 style="color: gold">Variable (P)</h1>
                <v-radio-group column>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="True (จริง)"
                  color="green"
                  :value="true"
                ></v-radio>
              </v-col>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="false (เท็จ)"
                  color="red"
                  :value="false"
                ></v-radio>
              </v-col>
              <v-col class="flex-center">
                <v-checkbox 
                class="black-label"
                label="Negation (นิเสธ)"
                color="#00e0ff"
              ></v-checkbox>
              </v-col>
            </v-radio-group>
          </v-col>
          <v-col cols="4">
            <h1 style="color: gold">Logic</h1>
            <v-radio-group column>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="And ^ (และ)"
                  color="green"
                  :value="true"
                ></v-radio>
              </v-col>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="or v (หรือ)"
                  color="red"
                  :value="false"
                ></v-radio>
              </v-col>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="false (เท็จ)"
                  color="red"
                  :value="false"
                ></v-radio>
              </v-col>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="false (เท็จ)"
                  color="red"
                  :value="false"
                ></v-radio>
              </v-col>
            </v-radio-group>
          </v-col>
          <v-col cols="4">
            <h1 style="color: gold">Variable (Q)</h1>
            <v-radio-group column>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="True (จริง)"
                  color="green"
                  :value="true"
                ></v-radio>
              </v-col>
              <v-col class="flex-center">
                <v-radio
                  class="black-label mt-5"
                  label="false (เท็จ)"
                  color="red"
                  :value="false"
                ></v-radio>
              </v-col>
              <v-col class="flex-center">
                <v-checkbox 
                class="black-label"
                label="Negation (นิเสธ)"
                color="#00e0ff"
              ></v-checkbox>
              </v-col>
            </v-radio-group>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </div>
</template>

<script>
export default {
  data() {
    return {
    };
  },
};
</script>

<style>
#app {
  background: rgb(0, 0, 0);
  background: linear-gradient(
    90deg,
    rgba(0, 0, 0, 1) 0%,
    rgba(19, 45, 45, 1) 30%,
    rgba(35, 77, 82, 1) 65%,
    rgba(100, 124, 87, 1) 100%
  );
}
.black-label label {
  color: rgb(255, 255, 255) !important;
  font-size: 20px;
}
.flex-center {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>