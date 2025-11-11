<template>
  <div class="about-page">
    <nav class="navbar">
      <div class="nav-content">
        <h2>關於我們</h2>
        <div class="nav-links">
          <router-link v-if="isAuthenticated" to="/welcome">歡迎頁面</router-link>
          <router-link v-else to="/">登入</router-link>
        </div>
      </div>
    </nav>
    
    <div class="content">
      <div class="about-card">
        <h1>關於我們</h1>
        <div class="about-content">
          <section>
            <h3>專案介紹</h3>
            <p>這是一個使用 Vite + Vue + SCSS 建立的簡單登入系統。</p>
          </section>
          
          <section>
            <h3>技術堆疊</h3>
            <ul>
              <li>Vue 3 - 前端框架</li>
              <li>Vite - 建置工具</li>
              <li>Vue Router - 路由管理</li>
              <li>SCSS - CSS 預處理器</li>
            </ul>
          </section>
          
          <section>
            <h3>功能特色</h3>
            <ul>
              <li>簡單的登入系統</li>
              <li>路由保護機制</li>
              <li>環境變數配置 (開發/正式)</li>
              <li>自訂 Context Path 支援</li>
            </ul>
          </section>
          
          <section class="env-info">
            <h3>環境資訊</h3>
            <p><strong>當前模式:</strong> {{ mode }}</p>
            <p><strong>Context Path:</strong> {{ contextPath }}</p>
          </section>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const mode = ref(import.meta.env.MODE)
const contextPath = ref(import.meta.env.VITE_CONTEXT_PATH)
const isAuthenticated = computed(() => 
  localStorage.getItem('isAuthenticated') === 'true'
)
</script>

<style lang="scss" scoped>
.about-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  
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
      }
    }
  }
  
  .content {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: calc(100vh - 80px);
    padding: 2rem;
    
    .about-card {
      background: white;
      padding: 3rem;
      border-radius: 10px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
      max-width: 800px;
      width: 100%;
      
      h1 {
        color: #333;
        margin-bottom: 2rem;
        text-align: center;
        font-size: 2.5rem;
      }
      
      .about-content {
        section {
          margin-bottom: 2rem;
          
          h3 {
            color: #667eea;
            margin-bottom: 1rem;
            font-size: 1.5rem;
          }
          
          p {
            color: #666;
            line-height: 1.6;
            margin-bottom: 0.5rem;
          }
          
          ul {
            list-style-position: inside;
            color: #666;
            line-height: 2;
            
            li {
              padding-left: 1rem;
            }
          }
          
          &.env-info {
            background: #f5f5f5;
            padding: 1.5rem;
            border-radius: 5px;
            border-left: 4px solid #667eea;
            
            p {
              margin-bottom: 0.75rem;
              
              strong {
                color: #333;
              }
            }
          }
        }
      }
    }
  }
}
</style>
