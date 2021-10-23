<template>
  <div class="sing-up">
    <div class="sing-up__header">
      <h1>Регистрация</h1>
      <p>Уже есть аккаунт? <span class="mark">Войти</span></p>
    </div>
    <div class="sing-up__body">
      <e-field label="Имя" :error="validateName">
        <e-input v-model="name" placeholder="Введите Ваше имя" />
      </e-field>
      <e-field label="Email" :error="validateEmail">
        <e-input v-model="email" placeholder="Введите ваш email" />
      </e-field>
      <e-field label="Номер телефона" :error="validatePhone">
        <e-input v-model="phone" placeholder="Введите номер телефона" />
      </e-field>
      <e-field label="Номер телефона">
        <e-select v-model="language" :list="list" placeholder="Язык" />
      </e-field>
      <div class="inline">
        <e-checkbox v-model="check" />
        <p>Принимаю <span class="mark">условия</span> использования</p>
      </div>
    </div>
    <div class="sing-up__footer">
      <e-button :disabled="isCheck" />
    </div>
  </div>
</template>

<script>
export default {
  name: "sing-up",
  data: () => ({
    name: "",
    email: "",
    phone: "",
    language: "",
    check: false,
    list: [
      { value: "ru", label: "Русский" },
      { value: "en", label: "Английский" },
      { value: "cn", label: "Китайский" },
      { value: "sp", label: "Испанский" },
    ],
  }),
  computed: {
    validateName() {
      return this.validate(/^[a-zA-Z\s-]+$/, this.name);
    },
    validatePhone() {
      return this.validate(
        /^(\s*)?(\+)?([- _():=+]?\d[- _():=+]?){11}(\s*)?$/,
        this.phone
      );
    },
    validateEmail() {
      return this.validate(/\S+@\S+\.\S+/, this.email);
    },
    isCheck() {
      return (
        !this.check ||
        !this.language ||
        !(this.name && !this.validateName) ||
        !(this.phone && !this.validatePhone) ||
        !(this.email && !this.validateEmail)
      );
    },
  },
  methods: {
    validate(reg, text) {
      return text
        ? reg.test(text)
          ? ""
          : "Введено не корректное значение"
        : "";
    },
  },
};
</script>

<style lang="scss" scoped>
.sing-up {
  &__header {
    margin-bottom: 58px;
    h1 {
      font-style: normal;
      font-weight: bold;
      font-size: 34px;
      line-height: 44px;
      color: #2c2738;
      margin-bottom: 8px;
    }
    p {
      font-style: normal;
      font-weight: normal;
      font-size: 16px;
      line-height: 22px;
    }
  }
  &__body {
    .inline {
      display: flex;
      align-items: center;
      margin-bottom: 40px;
      p {
        padding: 0 0 0 8px;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 21px;
      }
    }
  }
}
.mark {
  color: #0880ae;
  cursor: pointer;
}
</style>


