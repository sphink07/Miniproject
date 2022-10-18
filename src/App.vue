<template>
  <div>
    <v-app>
      <v-alert border="right" type="error" elevation="2" :value="alertV">
        Fusce commodo aliquam arcu. Pellentesque posuere. Phasellus tempus.
        Donec posuere vulputate arcu.
      </v-alert>
      <v-container style="text-align: center">
        <h1 style="color: gold; font-size: 50px">Truth Value Basics</h1>
        <span style="color: aliceblue; font-size: 20px">
          ──── Make by Nattanon ────
        </span>
        <v-row class="mt-5">
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
        <v-row>
          <v-container>
            <v-col>
              <v-row>
                <v-col>
                  <p style="font-size: 50px" class="white--text">
                    <span v-if="this.Pbox">~</span>
                    P(
                    <span style="font-size: 50px; color: gold">{{
                      this.PVF
                    }}</span>
                    )
                  </p>
                </v-col>
                <v-col>
                  <p style="font-size: 50px" class="white--text">
                    (
                    <span style="font-size: 50px; color: gold">{{
                      this.LVF
                    }}</span>
                    )
                  </p>
                </v-col>
                <v-col>
                  <p style="font-size: 50px" class="white--text">
                    <span v-if="this.Qbox">~</span>
                    Q(
                    <span style="font-size: 50px; color: gold">{{
                      this.QVF
                    }}</span>
                    )
                  </p>
                </v-col>
              </v-row>
            </v-col>
            <v-col>
              <v-btn @click="ClickBTN()" class="mr-6" width="100"
                >Confirm</v-btn
              >
              <v-btn @click="reset()" width="100">{{ this.result }}</v-btn>
            </v-col>
          </v-container>
        </v-row>
      </v-container>
      <v-overlay :z-index="0" :value="overlay" opacity="0.85">
        <v-alert type="success" v-if="this.result == true"></v-alert>
        <v-alert
          type="error"
          icon="mdi-close-circle"
          v-if="this.result == false"
        ></v-alert>
        <v-btn class="white--text" color="teal" @click="overlay = false">
          Hide Overlay
        </v-btn>
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
      alertV:false,
    };
  },
  methods: {
    ClickBTN() {
      if(this.Pvarlue == null || this.Qvarlue == null || this.LogicValue == null){
        this.alertV = true
        setTimeout(() => {
          this.alertV = false;
            }, 1500);
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
      this.btnclick = false;
    },
    Alert(){
      
    }
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