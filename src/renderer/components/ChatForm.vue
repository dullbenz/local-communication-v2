<template>
  <div
    class="form"
    :class="{ smaller: smaller, 'no-icon': noIcon }"
  >
    <input
      :value="filePath || value"
      class="form__input"
      type="text"
      :required="required"
      :placeholder="placeholder"
      @keyup.enter="submitMessage"
      @input="(e) => $emit('input', e.target.value)"
    >
    <div
      v-if="withAttachment"
      class="attachment form__submit"
    >
      <i
        id="btn"
        class="bx bxs-file-blank bx-sm"
        style="color: #636363;"
      />
      <input
        id="file"
        type="file"
        name="file"
        @change="(e) => {
          filePath = e.target.files[0] ? `file:///${e.target.files[0].path}?///` : '';
          $emit('input', filePath)
        }"
      >
    </div>
    <div
      class="form__submit"
      @click="submitMessage"
    >
      <svg
        v-if="!noIcon"
        width="30"
        height="30"
        viewBox="0 0 68 68"
        fill="#636363"
        xmlns="http://www.w3.org/2000/svg"
      >
        <g clip-path="url(#clip0_26_10)">
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M48.0833 19.799C48.619 20.3347 48.806 21.127 48.5665 21.8457L35.8385 60.0294C35.5946 60.7614 34.9513 61.2877 34.1855 61.382C33.4198 61.4763 32.6681 61.1217 32.2539 60.4707L22.593 45.2893L7.41158 35.6285C6.76065 35.2142 6.40604 34.4625 6.50031 33.6968C6.59458 32.931 7.12092 32.2878 7.85287 32.0438L46.0366 19.3159C46.7553 19.0763 47.5476 19.2633 48.0833 19.799ZM26.5903 44.1204L33.3726 54.7782L42.0926 28.6181L26.5903 44.1204ZM39.2642 25.7897L23.7619 41.292L13.1041 34.5097L39.2642 25.7897Z"
            fill=""
          />
        </g>
        <defs>
          <clipPath id="clip0_26_10">
            <rect
              width="48"
              height="48"
              fill="white"
              transform="translate(33.9412) rotate(45)"
            />
          </clipPath>
        </defs>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatForm",
  props: {
    noIcon: {
      type: Boolean,
      default: false,
    },
    smaller: {
      type: Boolean,
      default: false,
    },
    placeholder: {
      type: String,
      default: "Type a message",
    },
    value: {
      type: String,
      default: "",
    },
    required: {
      type: Boolean,
      default: false,
    },
    withAttachment: {
      type: Boolean,
      default: false,
    },
  },
  emits: ["input"],
  data() {
    return {
      msg: "",
      filePath: ""
    };
  },
  methods: {
    submitMessage() {
      if (this.value) {
        this.$emit("submit-message");
      }
      return;
    },
  },
};
</script>

<style scoped>
/* Google Font Link */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap");
@import url("https://unpkg.com/boxicons@2.0.7/css/boxicons.min.css");

.form {
  display: flex;
  justify-content: space-between;
  padding: 8px 16px;
  background: #1d1b31;
  border-radius: 30px 30px 24px 24px;
  border: 2px solid #636363;
  box-shadow: 0px -5px 30px rgba(0, 0, 0, 0.05);
}
.form__input {
  border: none;
  padding: 0.5rem;
  font-size: 16px;
  width: calc(100% - 60px);
  background-color: transparent;
  color: #636363;
}

.smaller .form__input {
  padding: 0 8px;
  height: unset;
}

.no-icon .form__input {
  width: 100%;
}
.form__input:focus {
  outline: none;
}
.form__submit {
  display: flex;
  align-items: center;
  cursor: pointer;
}

.attachment {
  position: relative;
  overflow: hidden;
  cursor: pointer;
  padding-top: 2px;
  margin-right: 2px;
}

.attachment i {
  cursor: pointer;
}

.attachment input[type="file"] {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  opacity: 0;
  cursor: pointer;
  background: red;
  
}

svg {
  transition: 0.3s;
}

svg:hover {
  fill: #cccccc;
}
</style>
