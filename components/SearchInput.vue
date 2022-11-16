<template>
    <v-text-field class="csSearchInput"
                  :disabled="isDisabled"
                  :error="hasError"
                  :label="label"
                  :messages="message"
                  v-on="{ ...$listeners }"
                  style="max-height: 50px"
                  outlined
                  >
      <template v-slot:append>
        <div class="csSearchInput__icon--search" :class="{ 'csSearchInput__icon--search--disabled' : isDisabled}" @click="clicked">
          <img width="24" height="24" svg-inline src="../assets/icons/search.svg" />
        </div>
      </template>
    </v-text-field>
  </template>
  
  <script>
  export default {
    name: 'csSearchInput',
    props: {
      label: {
        type: String,
      },
      isDisabled: {
        type: Boolean
      },
      hasError: {
        type: Boolean
      },
      message: {
        type: String
      },
    },
  
    methods: {
      clicked() {
        if (this.isDisabled) return
  
        this.$emit('search')
      }
    }
  }
  </script>
  
  <style lang="scss">
  
  .csSearchInput {
    .v-input__slot {
      min-height: unset !important;
    }
    .v-input__append-inner {
      margin-top: 0 !important;
    }
  
    &__icon {
      &--search {
          background-color: blue;
          padding: 10px;
          border-bottom-right-radius: 4px;
          border-top-right-radius: 4px;
          margin-right: -12px;


        &:hover {
          background-color: gray;
          cursor: pointer;
        }
  
        &--disabled {
          background-color: gray;
  
          &:hover {
            cursor: not-allowed;
            background-color: gray;
          }
        }
      }
    }
  }
  </style>