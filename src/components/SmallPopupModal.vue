<template>
    <div class="popup-message-background flex-center-align">
      <div class="popup-message">
        <div class="popup-header">
          <span>{{ title }}</span>
          <div v-if="showClose" class="close-button active-md" @click="sendResponse">
             X
          </div>
        </div>
        <slot />
      </div>
    </div>
  </template>
  
  <script>
  
  export default {
    data () {
        return {
            showClose: true
        }
    },
    props: {
      title: {
        type: String,
        require: true,
        default: () => 'Campaign Details'
      }
    },
    methods: {
      sendResponse () {
        this.$emit('close')
      }
    },
  }
  
  </script>
  
    <style lang="scss" scoped>
    @import '../styles.scss';
    .popup-message-background {
      width: 100vw;
      height: 100vh;
      position: fixed;
      top: 0;
      left: 0;
      z-index: 4;
      background-color: #00000033;
  
      .popup-message {
        overflow: hidden;
        width: fit-content;
        padding: 1rem;
        height: fit-content;
        border-radius: 30px;
        box-shadow: 0px 8px 16px 0px #00000040;
        background-color: #FFFFFF;
        color: black;
        .popup-header {
          margin-left: 20px;
          width: 95%;
          display: flex;
          justify-content: space-between;
          span {
            font-size: 1.4em;
          }
          .close-button {
            align-self: flex-end;
          margin: rem-calc(5) rem-calc(7);
          cursor: pointer;
          .icon {
            fill: red($color: #000000);
          }
        }
      }
  
        .description-section {
          flex: 1;
          display: flex;
          flex-direction: column;
          justify-content: center;
          width: calc(100% - #{rem-calc(217)});
          padding: 0 rem-calc(3) 0 rem-calc(22);
  
          .main-text {
            font-size: rem-calc(18);
            font-weight: bold;
            margin-bottom: rem-calc(2);
          }
  
          .sub-text {
            font-size: rem-calc(11);
          }
        }
  
        .button-section {
          padding: rem-calc(16) rem-calc(28);
  
          .cancel-button {
            margin-right: rem-calc(12);
            margin-left: 20px;
          }
        }
  
        &.confirm {
          background-size: rem-calc(164) rem-calc(164);
          background-position-x: calc(100% - #{rem-calc(7)});
          background-position-y: rem-calc(9);
  
          .description-section {
            width: calc(100% - #{rem-calc(171)});
          }
  
          .button-section {
            justify-content: flex-end;
          }
        }
  
        &.dark {
          background-color: #1B1D2C;
          color: #fff;
  
          .close-button {
            .icon{
              fill: rgba(255, 255, 255, 0.5);
            }
  
            &:hover .icon{
              fill: red
            }
          }
  
          .light-btn:active {
            color: black;
          }
        }
      }
    }
    .flex-center-align {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
    </style>
  