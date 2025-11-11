<template>
  <div class="welcome-page">
    <nav class="navbar">
      <div class="nav-content">
        <h2>歡迎頁面</h2>
        <div class="nav-links">
          <router-link to="/about">關於我們</router-link>
          <button @click="handleLogout" class="logout-btn">登出</button>
        </div>
      </div>
    </nav>
    
    <div class="content">
      <div class="welcome-card">
        <h1>歡迎, {{ username }}!</h1>
        <p>您已成功登入系統。</p>
        <div class="info">
          <p><strong>當前環境:</strong> {{ mode }}</p>
          <p><strong>Context Path:</strong> {{ contextPath }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const username = ref('')
const mode = ref(import.meta.env.MODE)
const contextPath = ref(import.meta.env.VITE_CONTEXT_PATH)

onMounted(() => {
  username.value = localStorage.getItem('username') || '訪客'
})

const handleLogout = () => {
  localStorage.removeItem('isAuthenticated')
  localStorage.removeItem('username')
  router.push('/')
}
</script>

<style lang="scss" scoped>
.welcome-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  
  .navbar {
    background: white;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    
    .nav-content {
      max-width: 1200px;
      margin: 0 auto;
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      
      h2 {
        color: #333;
        margin: 0;
      }
      
      .nav-links {
        display: flex;
        gap: 1rem;
        align-items: center;
        
        a {
          color: #667eea;
          text-decoration: none;
          font-weight: 500;
          padding: 0.5rem 1rem;
          border-radius: 5px;
          transition: background-color 0.3s;
          
          &:hover {
            background-color: #f0f0f0;
          }
        }
        
        .logout-btn {
          padding: 0.5rem 1rem;
          background: #f5576c;
          color: white;
          border: none;
          border-radius: 5px;
          font-weight: 600;
          cursor: pointer;
          transition: transform 0.2s;
          
          &:hover {
            transform: translateY(-2px);
          }
        }
      }
    }
  }
  
  .content {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: calc(100vh - 80px);
    padding: 2rem;
    
    .welcome-card {
      background: white;
      padding: 3rem;
      border-radius: 10px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
      text-align: center;
      max-width: 600px;
      
      h1 {
        color: #333;
        margin-bottom: 1rem;
        font-size: 2.5rem;
      }
      
      p {
        color: #666;
        font-size: 1.2rem;
        margin-bottom: 1rem;
      }
      
      .info {
        margin-top: 2rem;
        padding-top: 2rem;
        border-top: 2px solid #e0e0e0;
        text-align: left;
        
        p {
          margin-bottom: 0.75rem;
          font-size: 1rem;
          
          strong {
            color: #333;
          }
        }
      }
    }
  }
}
</style>
