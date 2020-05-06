<template>
    <div>
      <div class="md-modal modal-msg md-modal-transition" v-bind:class="{'md-show':(mdShow || addrShow || toAdd)}">
        <div class="md-modal-inner">
          <div class="md-top">
            <button class="md-close" @click="closeModal">Close</button>
          </div>
          <div class="md-content">
            <!-- 修改地址 -->
            <div class="confirm-tips" v-if="addrShow">
              收件人姓名:<slot name="addrName"></slot>
            </div>
            <div class="confirm-tips" v-if="addrShow">
              详细地址:<slot name="addrInfo"></slot>
            </div>
            <div class="confirm-tips" v-if="addrShow">
              联系电话:<slot name="addrTel"></slot>
            </div>
            <!-- 添加地址 -->
            <div class="confirm-tips" v-if="toAdd">
              收件人姓名:<slot name="addrNameAdd"></slot>
            </div>
            <div class="confirm-tips" v-if="toAdd">
              详细地址:<slot name="addrInfoAdd"></slot>
            </div>
            <div class="confirm-tips" v-if="toAdd">
              联系电话:<slot name="addrTelAdd"></slot>
            </div>
            <!-- 提示信息 -->
            <div class="confirm-tips" v-if="mdShow">
              <slot name="message"></slot>
            </div>
            <div class="btn-wrap">
              <slot name="btnGroup"></slot>
            </div>
          </div>
        </div>
      </div>
      <div class="md-overlay" v-if="(mdShow || addrShow || toAdd)" @click="closeModal"></div>
    </div>
</template>
<style>

</style>
<script>
    export default{
        props:["mdShow","addrShow","toAdd"],
        data(){
            return{
                msg:'hello vue'
            }
        },
        methods:{
          closeModal(){
            this.$emit("close");
          }
        }
    }
</script>
