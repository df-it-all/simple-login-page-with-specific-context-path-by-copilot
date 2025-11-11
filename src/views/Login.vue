<template>
  <div class="login-page">
    <div class="login-container">
      <h1>登入</h1>
      <form @submit.prevent="handleLogin">
        <div class="form-group">
          <label for="username">使用者名稱</label>
          <input 
            id="username" 
            v-model="username" 
            type="text" 
            placeholder="請輸入使用者名稱"
            required
          />
        </div>
        <div class="form-group">
          <label for="password">密碼</label>
          <input 
            id="password" 
            v-model="password" 
            type="password" 
            placeholder="請輸入密碼"
            required
          />
        </div>
        <button type="submit" class="login-btn">登入</button>
      </form>
      <div class="links">
        <router-link to="/about">關於我們</router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const username = ref('')
const password = ref('')

const handleLogin = () => {
  // Simple login logic - accepts any username/password
  if (username.value && password.value) {
    localStorage.setItem('isAuthenticated', 'true')
    localStorage.setItem('username', username.value)
    router.push('/welcome')
  }
}
</script>

<style lang="scss" scoped>
.login-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  
  .login-container {
    background: white;
    padding: 2.5rem;
    border-radius: 10px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
    width: 100%;
    max-width: 400px;
    
    h1 {
      text-align: center;
      color: #333;
      margin-bottom: 2rem;
      font-size: 2rem;
    }
    
    .form-group {
      margin-bottom: 1.5rem;
      
      label {
        display: block;
        margin-bottom: 0.5rem;
        color: #555;
        font-weight: 500;
      }
      
      input {
        width: 100%;
        padding: 0.75rem;
        border: 2px solid #e0e0e0;
        border-radius: 5px;
        font-size: 1rem;
        transition: border-color 0.3s;
        
        &:focus {
          outline: none;
          border-color: #667eea;
        }
      }
    }
    
    .login-btn {
      width: 100%;
      padding: 0.75rem;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: transform 0.2s;
      
      &:hover {
        transform: translateY(-2px);
      }
      
      &:active {
        transform: translateY(0);
      }
    }
    
    .links {
      margin-top: 1.5rem;
      text-align: center;
      
      a {
        color: #667eea;
        text-decoration: none;
        font-weight: 500;
        
        &:hover {
          text-decoration: underline;
        }
      }
    }
  }
}
</style>
