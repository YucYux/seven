/* eslint-disable */
<template>
  <div>
    <Button type="success" @click="modal1 = true" ghost>登录</Button>
    <Modal
      v-model="modal1"
      title="Welcome to PKUOnlineExamPlatform"
      draggable="true"
      ok-text="登录"
      width="360px"
      cancle-text="取消"
      @on-ok="ok"
      @on-cancel="cancel"
    >
      <div>
        <Input
          prefix="ios-contact"
          v-model="v_username"
          placeholder="Username"
          style="width: auto"
        ></Input>
      </div>
      <div style="margin-top: 6px">
        <Input
          prefix="ios-lock"
          v-model="v_password"
          placeholder="Password"
          type="password"
          style="width: auto"
        ></Input>
      </div>
    </Modal>
  </div>
</template>
<script>
import api from '../api.js'
import store from '../store'

export default {
  data () {
    return {
      modal1: false,
      v_username: '',
      v_password: ''
    }
  },
  methods: {
    ok () {
      api.APIlogin(this.v_username, this.v_password).then(
        (result) => {
          store.dispatch(
            'changeFooterInfo',
            '欢迎，' + store.getters.getUsername
          );
          this.$Notice.success({
            title: '登录成功',
            desc: '您的身份是：' + store.getters.getUsertype
          });
          api.APIgetAnnouncementList();
        },
        (error) => {
          this.$Notice.error({
            title: '登录失败',
            desc: ''
          })
          console.log(error)
        }
      )
      this.v_username = this.v_password = ''
    },
    cancel () {
      this.$Message.info('Clicked cancel')
      this.v_username = this.v_password = ''
    }
  }
}
</script>
