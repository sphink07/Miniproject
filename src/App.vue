<template>
  <div>
    <v-app>
      <v-alert
        style="z-index: 1; position: absolute; width: 100vw"
        border="right"
        type="error"
        elevation="6"
        :value="alertV"
      >
        Please select complete information.
      </v-alert>
      <v-container style="text-align: center; z-index: 0">
        <h1 style="color: gold; font-size: 50px">Truth Value Basics</h1>
        <span style="color: aliceblue; font-size: 20px">
          ──── Make by Nattanon ────
        </span>
        <!-- ────────────────────────────────────────────────────────────── MD ────────────────────────────────────────────────────────────── -->
        <v-row class="mt-5 hidden-sm-and-down">
          <v-col cols="4">
            <h1 style="color: gold">Variable (P)</h1>
            <v-col class="flex-center">
              <v-select
                v-model="Pvarlue"
                :items="items"
                label="click here for select"
                solo
                style="width: 15vw"
              >
              </v-select>
              <v-checkbox
                v-model="Pbox"
                style="margin-top: -10px"
                class="black-label"
                label="Negation ( ~ นิเสธ)"
                color="#00e0ff"
              ></v-checkbox>
            </v-col>
          </v-col>
          <v-col cols="4">
            <h1 style="color: gold">Logic</h1>
            <v-col class="flex-center">
              <v-select
                v-model="LogicValue"
                :items="Logic"
                label="click here for select"
                solo
                style="width: 15vw"
              >
              </v-select>
            </v-col>
          </v-col>
          <v-col cols="4">
            <h1 style="color: gold">Variable (Q)</h1>
            <v-col class="flex-center">
              <v-select
                v-model="Qvarlue"
                :items="items"
                label="click here for select"
                solo
                style="width: 15vw"
              >
              </v-select>
              <v-checkbox
                v-model="Qbox"
                style="margin-top: -10px"
                class="black-label"
                label="Negation ( ~ นิเสธ)"
                color="#00e0ff"
              ></v-checkbox>
            </v-col>
          </v-col>
        </v-row>
        <v-row class="hidden-sm-and-down">
          <v-container>
            <v-col>
              <v-container style="width: 50vw">
                <v-row>
                  <v-col>
                    <p style="font-size: 40px" class="white--text">
                      <span v-if="this.Pbox">~</span>
                      P(
                      <span style="font-size: 40px; color: gold">{{
                        this.PVF
                      }}</span>
                      )
                    </p>
                  </v-col>
                  <v-col>
                    <p style="font-size: 40px" class="white--text">
                      (
                      <span style="font-size: 40px; color: gold">{{
                        this.LVF
                      }}</span>
                      )
                    </p>
                  </v-col>
                  <v-col>
                    <p style="font-size: 40px" class="white--text">
                      <span v-if="this.Qbox">~</span>
                      Q(
                      <span style="font-size: 40px; color: gold">{{
                        this.QVF
                      }}</span>
                      )
                    </p>
                  </v-col>
                </v-row>
              </v-container>
            </v-col>
            <v-col style="margin-top: 50px">
              <v-btn
                @click="ClickBTN()"
                class="mr-10"
                width="100"
                style="
                  color: mediumspringgreen;
                  background-color: lightslategray;
                "
                >Confirm</v-btn
              >
              <v-btn
                @click="reset()"
                width="100"
                style="color: linen; background-color: lightslategray"
                >Reset</v-btn
              >
            </v-col>
          </v-container>
        </v-row>
        <!-- ────────────────────────────────────────────────────────────── SM ────────────────────────────────────────────────────────────── -->
        <v-row class="mt-5 hidden-md-and-up">
          <v-col cols="12">
            <h1 style="color: gold">Variable (P)</h1>
            <v-col class="flex-center">
              <v-select
                v-model="Pvarlue"
                :items="items"
                label="click here for select"
                solo
                style="width: 45vw"
              >
              </v-select>
              <v-checkbox
                v-model="Pbox"
                style="margin-top: -10px"
                class="black-label"
                label="Negation ( ~ นิเสธ)"
                color="#00e0ff"
              ></v-checkbox>
            </v-col>
          </v-col>
          <v-col style="margin-top:-15px" cols="12">
            <h1 style="color: gold">Logic</h1>
            <v-col class="flex-center">
              <v-select
                v-model="LogicValue"
                :items="Logic"
                label="click here for select"
                solo
                style="width:45vw"
              >
              </v-select>
            </v-col>
          </v-col>
          <v-col cols="12">
            <h1 style="color: gold">Variable (Q)</h1>
            <v-col class="flex-center">
              <v-select
                v-model="Qvarlue"
                :items="items"
                label="click here for select"
                solo
                style="width: 45vw"
              >
              </v-select>
              <v-checkbox
                v-model="Qbox"
                style="margin-top: -10px"
                class="black-label"
                label="Negation ( ~ นิเสธ)"
                color="#00e0ff"
              ></v-checkbox>
            </v-col>
          </v-col>
        </v-row>
        <v-row class="hidden-md-and-up">
          <v-container>
            <v-col>
                <v-row>
                  <v-col cols="5">
                    <p style="font-size: 30px" class="white--text">
                      <span v-if="this.Pbox">~</span>
                      P
                      <v-spacer></v-spacer>
                      (
                      <span style="font-size: 30px; color: gold">{{
                        this.PVF
                      }}</span>
                      )
                    </p>
                  </v-col>
                  <v-col cols="2">
                    <p style="font-size: 30px" class="white--text">
                      
                      <span style="font-size: 30px; color: gold">{{
                        this.LVF
                      }}</span>
                      
                    </p>
                  </v-col>
                  <v-col cols="5">
                    <p style="font-size: 30px" class="white--text">
                      <span v-if="this.Qbox">~</span>
                      Q
                      <v-spacer></v-spacer>
                      (
                      <span style="font-size: 30px; color: gold">{{
                        this.QVF
                      }}</span>
                      )
                    </p>
                  </v-col>
                </v-row>
            </v-col>
            <v-col style="margin-top: 50px">
              <v-btn
                @click="ClickBTN()"
                class="mr-10"
                width="100"
                style="
                  color: mediumspringgreen;
                  background-color: lightslategray;
                "
                >Confirm</v-btn
              >
              <v-btn
                @click="reset()"
                width="100"
                style="color: linen; background-color: lightslategray"
                >Reset</v-btn
              >
            </v-col>
          </v-container>
        </v-row>
        <!-- ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── -->
      </v-container>
      <v-overlay
        :z-index="0"
        :value="overlay"
        opacity="0.95"
        @click="overlay = false"
      >
        <p style="text-align: center; font-size: 40px; font-weight: bold">
          Your answer :
        </p>
        <v-alert
          style="font-size: 18px"
          type="success"
          v-if="this.result == true"
          >TRUE</v-alert
        >
        <v-alert
          style="font-size: 18px"
          type="error"
          icon="mdi-close-circle"
          v-if="this.result == false"
          >FALSE</v-alert
        >
      </v-overlay>
    </v-app>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: ["true (จริง)", "false (เท็จ)"],
      Logic: [
        "And(และ)",
        "Or(หรือ)",
        "Only if(ถ้า..แล้ว)",
        "If and only if(ก็ต่อเมื่อ)",
      ],
      LogicValue: null,
      Pvarlue: null,
      Qvarlue: null,
      PVF: null,
      QVF: null,
      LVF: null,
      Pbox: false,
      Qbox: false,
      result: null,
      overlay: false,
      alertV: false,
    };
  },
  methods: {
    ClickBTN() {
      if (
        this.Pvarlue == null ||
        this.Qvarlue == null ||
        this.LogicValue == null
      ) {
        this.alertV = true;
        setTimeout(() => {
          this.alertV = false;
        }, 2000);
      } else {
        this.overlay = true;
        switch (this.LogicValue) {
          case "And(และ)":
            this.AND();
            break;
          case "Or(หรือ)":
            this.OR();
            break;
          case "Only if(ถ้า..แล้ว)":
            this.IF();
            break;
          case "If and only if(ก็ต่อเมื่อ)":
            this.Between();
            break;
        }
      }
    },
    chackP() {
      if (this.Pbox == false) {
        switch (this.Pvarlue) {
          case "true (จริง)":
            this.PVF = true;
            break;
          case "false (เท็จ)":
            this.PVF = false;
            break;
        }
      } else if (this.Pbox == true) {
        switch (this.Pvarlue) {
          case "true (จริง)":
            this.PVF = false;
            break;
          case "false (เท็จ)":
            this.PVF = true;
            break;
        }
      }
    },
    chackQ() {
      if (this.Qbox == false) {
        switch (this.Qvarlue) {
          case "true (จริง)":
            this.QVF = true;
            break;
          case "false (เท็จ)":
            this.QVF = false;
            break;
        }
      } else if (this.Qbox == true) {
        switch (this.Qvarlue) {
          case "true (จริง)":
            this.QVF = false;
            break;
          case "false (เท็จ)":
            this.QVF = true;
            break;
        }
      }
    },
    chackLogic() {
      switch (this.LogicValue) {
        case "And(และ)":
          this.LVF = "^";
          break;
        case "Or(หรือ)":
          this.LVF = "v";
          break;
        case "Only if(ถ้า..แล้ว)":
          this.LVF = "→";
          break;
        case "If and only if(ก็ต่อเมื่อ)":
          this.LVF = "↔";
          break;
      }
    },
    AND() {
      this.result = this.PVF && this.QVF;
    },
    OR() {
      this.result = this.PVF || this.QVF;
    },
    IF() {
      if (this.PVF == true && this.QVF == false) {
        this.result = false;
      } else {
        this.result = true;
      }
    },
    Between() {
      if (this.PVF === this.QVF) {
        this.result = true;
      } else {
        this.result = false;
      }
    },
    reset() {
      this.Pvarlue = null;
      this.Qvarlue = null;
      this.LogicValue = null;
      this.Pbox = false;
      this.Qbox = false;
      this.PVF = null;
      this.QVF = null;
      this.LVF = null;
    },
  },
  updated() {
    this.chackP();
    this.chackQ();
    this.chackLogic();
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
.colorover {
  background: rgb(0, 0, 0);
  background: linear-gradient(
    90deg,
    rgba(0, 0, 0, 1) 0%,
    rgba(19, 45, 45, 1) 30%,
    rgba(35, 77, 82, 1) 65%,
    rgba(100, 124, 87, 1) 100%
  );
}
</style>