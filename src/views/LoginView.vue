<template>
  <div class="login-container">
    <n-input
      v-model:value="password"
      size="large"
      round
      placeholder="大王口令"
      class="centered-input"
      @keyup.enter="handleLogin"
    >
      <template #suffix>
        <n-button
          quaternary
          circle
          @click="handleLogin"
          class="send-button"
        >
          <template #icon>
            <n-icon>
              <svg viewBox="0 0 24 24" width="20" height="20">
                <path fill="currentColor" d="M2,21L23,12L2,3V10L17,12L2,14V21Z" />
              </svg>
            </n-icon>
          </template>
        </n-button>
      </template>
    </n-input>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const password = ref('')
const errorMessage = ref('')

const handleLogin = () => {
  errorMessage.value = ''

  // 硬编码密码验证
  if (password.value === '我是步步大王') {
    // 登录成功，跳转到首页
    router.push('/home')
  } else {
    errorMessage.value = '口令错误'
  }
}
</script>

<style scoped>
.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
  position: fixed;
  top: 0;
  left: 0;
}

.centered-input {
  width: 400px;
}

.send-button {
  margin-right: 8px;
}

.send-button:hover {
  background-color: rgba(0, 0, 0, 0.1);
}

.centered-input :deep(input) {
  text-align: center !important;
}

.centered-input :deep(.n-input__input-el) {
  text-align: center !important;
}

.centered-input :deep(.n-input) {
  text-align: center !important;
}

/* 更通用的选择器 */
.centered-input :deep(*) {
  text-align: center !important;
}

</style>
