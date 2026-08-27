<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PakTutor · Mathematics Hub · Premium Edition</title>
  <!-- Font Awesome 6 (free) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- EmailJS for sending emails -->
  <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
  <style>
    :root {
      --primary: #0a0a0a;
      --secondary: #1a1a2e;
      --accent: #00ff88;
      --accent2: #ff006e;
      --accent3: #00d4ff;
      --accent4: #ffd700;
      --gradient1: linear-gradient(135deg, #00ff88, #00d4ff);
      --gradient2: linear-gradient(135deg, #ff006e, #ffd700);
      --gradient3: linear-gradient(135deg, #00d4ff, #ff006e);
      --text-primary: #ffffff;
      --text-secondary: #b0b0b0;
      --text-dark: #0a0a0a;
      --bg-body: #0a0a0a;
      --bg-card: rgba(26, 26, 46, 0.9);
      --shadow-neon: 0 0 20px rgba(0, 255, 136, 0.3);
      --shadow-neon2: 0 0 20px rgba(255, 0, 110, 0.3);
      --shadow-neon3: 0 0 20px rgba(0, 212, 255, 0.3);
      --border-radius-sm: 8px;
      --border-radius-md: 16px;
      --border-radius-lg: 24px;
      --border-radius-xl: 32px;
      --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', 'Segoe UI', system-ui, sans-serif;
    }

    body {
      background: var(--bg-body);
      min-height: 100vh;
      position: relative;
      overflow-x: hidden;
    }

    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: radial-gradient(ellipse at 20% 50%, rgba(255, 0, 110, 0.1) 0%, transparent 50%),
                  radial-gradient(ellipse at 80% 50%, rgba(0, 255, 136, 0.1) 0%, transparent 50%),
                  radial-gradient(ellipse at 50% 20%, rgba(0, 212, 255, 0.1) 0%, transparent 50%);
      pointer-events: none;
      z-index: 0;
    }

    body::after {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-image: linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
                        linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
      background-size: 50px 50px;
      pointer-events: none;
      z-index: 1;
    }

    .auth-container {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 2rem;
      position: relative;
      z-index: 2;
    }

    .auth-box {
      background: var(--bg-card);
      border-radius: var(--border-radius-lg);
      padding: 3rem;
      width: 100%;
      max-width: 420px;
      box-shadow: var(--shadow-neon);
      border: 1px solid rgba(0, 255, 136, 0.2);
      backdrop-filter: blur(20px);
      animation: slideUp 0.5s ease-out;
    }

    @keyframes slideUp {
      from { transform: translateY(50px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    .auth-header {
      text-align: center;
      margin-bottom: 2rem;
    }

    .auth-logo {
      width: 80px;
      height: 80px;
      background: var(--gradient1);
      border-radius: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 1rem;
      color: var(--text-dark);
      font-size: 2.5rem;
      box-shadow: var(--shadow-neon);
      animation: glow 2s ease-in-out infinite;
    }

    @keyframes glow {
      0%, 100% { box-shadow: 0 0 20px rgba(0, 255, 136, 0.5); }
      50% { box-shadow: 0 0 40px rgba(0, 255, 136, 0.8); }
    }

    .auth-header h1 {
      font-size: 2rem;
      font-weight: 700;
      background: var(--gradient1);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      margin-bottom: 0.5rem;
    }

    .auth-header p {
      color: var(--text-secondary);
      font-size: 0.9rem;
    }

    .auth-form {
      display: flex;
      flex-direction: column;
      gap: 1.2rem;
    }

    .form-group {
      position: relative;
    }

    .form-group label {
      display: block;
      margin-bottom: 0.5rem;
      color: var(--text-primary);
      font-weight: 500;
      font-size: 0.9rem;
    }

    .form-group input {
      width: 100%;
      padding: 0.8rem 1rem 0.8rem 2.5rem;
      background: rgba(0, 0, 0, 0.5);
      border: 2px solid rgba(0, 255, 136, 0.2);
      border-radius: var(--border-radius-sm);
      color: var(--text-primary);
      font-size: 1rem;
      transition: var(--transition);
    }

    .form-group input:focus {
      outline: none;
      border-color: var(--accent);
      box-shadow: var(--shadow-neon);
    }

    .form-group i {
      position: absolute;
      left: 0.8rem;
      bottom: 0.8rem;
      color: var(--accent);
    }

    .auth-btn {
      background: var(--gradient1);
      color: var(--text-dark);
      padding: 1rem;
      border: none;
      border-radius: var(--border-radius-sm);
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
      transition: var(--transition);
      margin-top: 1rem;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }

    .auth-btn:hover {
      box-shadow: var(--shadow-neon);
      transform: translateY(-2px);
    }

    .auth-links {
      text-align: center;
      margin-top: 1.5rem;
      display: flex;
      flex-direction: column;
      gap: 0.8rem;
    }

    .auth-link-btn {
      background: none;
      border: none;
      color: var(--accent3);
      cursor: pointer;
      font-size: 0.9rem;
      transition: var(--transition);
      text-decoration: underline;
    }

    .auth-link-btn:hover {
      color: var(--accent);
      text-shadow: 0 0 10px rgba(0, 255, 136, 0.5);
    }

    .contact-info {
      text-align: center;
      margin-top: 1.5rem;
      padding-top: 1.5rem;
      border-top: 1px solid rgba(255, 255, 255, 0.1);
    }

    .contact-info p {
      color: var(--text-secondary);
      font-size: 0.9rem;
      margin-bottom: 0.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }

    .contact-info i {
      color: var(--accent);
    }

    .contact-info a {
      color: var(--accent3);
      text-decoration: none;
      transition: var(--transition);
    }

    .contact-info a:hover {
      color: var(--accent);
      text-shadow: 0 0 10px rgba(0, 255, 136, 0.5);
    }

    .success-message {
      background: rgba(0, 255, 136, 0.1);
      border: 1px solid rgba(0, 255, 136, 0.3);
      color: var(--accent);
      padding: 1rem;
      border-radius: var(--border-radius-sm);
      text-align: center;
      margin-top: 1rem;
      display: none;
      animation: slideUp 0.3s ease-out;
    }

    .success-message.show {
      display: block;
    }

    .main-container {
      display: none;
      padding: 2rem;
      position: relative;
      z-index: 2;
      animation: fadeIn 0.5s ease-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .container {
      max-width: 1400px;
      margin: 0 auto;
    }

    .navbar {
      background: var(--bg-card);
      border-radius: var(--border-radius-xl);
      padding: 1.2rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 2rem;
      box-shadow: var(--shadow-neon);
      position: sticky;
      top: 1rem;
      z-index: 100;
      backdrop-filter: blur(20px);
      border: 1px solid rgba(0, 255, 136, 0.2);
    }

    .nav-brand {
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .nav-logo {
      width: 55px;
      height: 55px;
      background: var(--gradient1);
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--text-dark);
      font-size: 1.6rem;
      box-shadow: var(--shadow-neon);
      animation: glow 2s ease-in-out infinite;
    }

    .nav-title {
      font-size: 1.8rem;
      font-weight: 700;
      background: var(--gradient1);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .nav-subtitle {
      font-size: 0.85rem;
      color: var(--text-secondary);
    }

    .nav-actions {
      display: flex;
      gap: 0.8rem;
      align-items: center;
    }

    .user-info {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      color: var(--text-primary);
    }

    .user-info i {
      color: var(--accent);
    }

    .nav-btn {
      padding: 0.6rem 1.5rem;
      border-radius: var(--border-radius-xl);
      border: 2px solid transparent;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      font-size: 0.9rem;
    }

    .nav-btn-outline {
      background: transparent;
      border-color: var(--accent2);
      color: var(--accent2);
    }

    .nav-btn-outline:hover {
      background: var(--accent2);
      color: white;
      box-shadow: var(--shadow-neon2);
    }

    .hero {
      background: var(--bg-card);
      border-radius: var(--border-radius-lg);
      padding: 3rem;
      margin-bottom: 2rem;
      box-shadow: var(--shadow-neon3);
      position: relative;
      overflow: hidden;
      border: 1px solid rgba(0, 212, 255, 0.2);
    }

    .hero-content {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 2rem;
    }

    .hero-avatar {
      width: 110px;
      height: 110px;
      background: var(--gradient2);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3.5rem;
      color: white;
      box-shadow: var(--shadow-neon2);
      animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .hero-text {
      flex: 1;
    }

    .hero-text h1 {
      font-size: 2.5rem;
      font-weight: 700;
      color: var(--text-primary);
      margin-bottom: 0.5rem;
    }

    .hero-text h1 i {
      color: var(--accent4);
      animation: sparkle 1.5s ease-in-out infinite;
    }

    @keyframes sparkle {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.2); }
    }

    .hero-text p {
      font-size: 1.1rem;
      color: var(--text-secondary);
      margin-bottom: 1rem;
    }

    .hero-badges {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
    }

    .badge {
      padding: 0.5rem 1.5rem;
      border-radius: var(--border-radius-xl);
      font-weight: 600;
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      transition: var(--transition);
      cursor: pointer;
    }

    .badge:hover {
      transform: translateY(-3px);
    }

    .badge-primary {
      background: rgba(0, 255, 136, 0.1);
      color: var(--accent);
      border: 1px solid rgba(0, 255, 136, 0.3);
      box-shadow: var(--shadow-neon);
    }

    .badge-success {
      background: rgba(255, 0, 110, 0.1);
      color: var(--accent2);
      border: 1px solid rgba(255, 0, 110, 0.3);
      box-shadow: var(--shadow-neon2);
    }

    .badge-info {
      background: rgba(0, 212, 255, 0.1);
      color: var(--accent3);
      border: 1px solid rgba(0, 212, 255, 0.3);
      box-shadow: var(--shadow-neon3);
    }

    .filter-section {
      margin-bottom: 2rem;
    }

    .filter-tabs {
      display: flex;
      gap: 0.5rem;
      flex-wrap: wrap;
      background: var(--bg-card);
      padding: 0.5rem;
      border-radius: var(--border-radius-xl);
      box-shadow: var(--shadow-neon);
      backdrop-filter: blur(20px);
      border: 1px solid rgba(0, 255, 136, 0.2);
    }

    .filter-tab {
      padding: 0.7rem 1.5rem;
      border-radius: var(--border-radius-xl);
      border: none;
      background: transparent;
      cursor: pointer;
      transition: var(--transition);
      font-weight: 600;
      color: var(--text-secondary);
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .filter-tab:hover {
      color: var(--text-primary);
      background: rgba(255, 255, 255, 0.05);
    }

    .filter-tab.active {
      background: var(--gradient1);
      color: var(--text-dark);
      box-shadow: var(--shadow-neon);
    }

    .subjects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 1.5rem;
      margin-bottom: 2rem;
    }

    .subject-card {
      background: var(--bg-card);
      border-radius: var(--border-radius-md);
      padding: 1.5rem;
      box-shadow: var(--shadow-neon3);
      transition: var(--transition);
      cursor: pointer;
      position: relative;
      overflow: hidden;
      border: 1px solid rgba(0, 212, 255, 0.2);
    }

    .subject-card:hover {
      transform: translateY(-8px) scale(1.02);
      box-shadow: var(--shadow-neon);
    }

    .subject-card-header {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 1rem;
    }

    .subject-card-icon {
      width: 60px;
      height: 60px;
      background: var(--gradient4);
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.8rem;
      color: var(--text-dark);
      box-shadow: 0 0 15px rgba(255, 215, 0, 0.5);
      transition: var(--transition);
    }

    .subject-card:hover .subject-card-icon {
      transform: rotate(360deg);
    }

    .subject-card-title h3 {
      font-size: 1.2rem;
      font-weight: 700;
      color: var(--text-primary);
      margin-bottom: 0.3rem;
    }

    .subject-card-dept {
      font-size: 0.85rem;
      color: var(--text-secondary);
    }

    .subject-card-fee {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.8rem;
      background: rgba(255, 255, 255, 0.03);
      border-radius: var(--border-radius-sm);
      margin-bottom: 1rem;
    }

    .subject-card-fee span {
      font-size: 0.9rem;
      color: var(--text-secondary);
    }

    .subject-card-fee strong {
      font-size: 1.1rem;
      color: var(--accent4);
    }

    .subject-card-btn {
      width: 100%;
      padding: 0.8rem;
      background: var(--gradient1);
      color: var(--text-dark);
      border: none;
      border-radius: var(--border-radius-sm);
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      font-size: 0.95rem;
    }

    .subject-card-btn:hover {
      box-shadow: var(--shadow-neon);
      transform: scale(1.05);
    }

    .live-banner {
      background: var(--bg-card);
      border-radius: var(--border-radius-lg);
      padding: 2rem;
      margin-bottom: 2rem;
      box-shadow: var(--shadow-neon2);
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 2rem;
      background: linear-gradient(135deg, rgba(255, 0, 110, 0.1), rgba(0, 212, 255, 0.1));
      border: 1px solid rgba(255, 0, 110, 0.3);
    }

    .live-banner-left {
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .live-indicator {
      width: 15px;
      height: 15px;
      background: var(--accent2);
      border-radius: 50%;
      animation: pulse 1.5s infinite;
      box-shadow: 0 0 20px var(--accent2);
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.5); opacity: 0.5; }
    }

    .live-banner h3 {
      font-size: 1.5rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .live-banner p {
      color: var(--text-secondary);
    }

    .actions-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 1rem;
      margin-bottom: 2rem;
    }

    .action-btn {
      padding: 1.2rem;
      border-radius: var(--border-radius-md);
      border: none;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      font-size: 1rem;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.8rem;
      position: relative;
      overflow: hidden;
    }

    .action-btn::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
      transition: left 0.6s;
    }

    .action-btn:hover::before {
      left: 100%;
    }

    .action-btn:hover {
      transform: translateY(-5px) scale(1.05);
    }

    .action-btn-primary {
      background: var(--gradient1);
      color: var(--text-dark);
      box-shadow: var(--shadow-neon);
    }

    .action-btn-secondary {
      background: var(--gradient2);
      color: white;
      box-shadow: var(--shadow-neon2);
    }

    .action-btn-success {
      background: var(--gradient3);
      color: white;
      box-shadow: var(--shadow-neon3);
    }

    .action-btn-info {
      background: linear-gradient(135deg, #ffd700, #00ff88);
      color: var(--text-dark);
    }

    .contact-section {
      background: var(--bg-card);
      border-radius: var(--border-radius-lg);
      padding: 2rem;
      margin-bottom: 2rem;
      box-shadow: var(--shadow-neon);
      border: 1px solid rgba(0, 255, 136, 0.2);
    }

    .contact-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 1.5rem;
      margin-top: 1rem;
    }

    .contact-card {
      background: rgba(0, 0, 0, 0.3);
      border-radius: var(--border-radius-md);
      padding: 1.5rem;
      text-align: center;
      transition: var(--transition);
    }

    .contact-card:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-neon);
    }

    .contact-card i {
      font-size: 2rem;
      color: var(--accent);
      margin-bottom: 1rem;
    }

    .contact-card h4 {
      color: var(--text-primary);
      margin-bottom: 0.5rem;
    }

    .contact-card p, .contact-card a {
      color: var(--text-secondary);
      text-decoration: none;
      transition: var(--transition);
    }

    .contact-card a:hover {
      color: var(--accent);
    }

    .database-section {
      background: var(--bg-card);
      border-radius: var(--border-radius-lg);
      padding: 2rem;
      box-shadow: var(--shadow-neon3);
      border: 1px solid rgba(0, 212, 255, 0.2);
    }

    .database-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1rem;
    }

    .database-header h2 {
      font-size: 1.3rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .database-toggle {
      padding: 0.6rem 1.5rem;
      border-radius: var(--border-radius-xl);
      border: 2px solid var(--accent3);
      background: transparent;
      color: var(--accent3);
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
    }

    .database-toggle:hover {
      background: var(--accent3);
      color: var(--text-dark);
    }

    .database-content {
      display: none;
      margin-top: 1rem;
      padding: 1rem;
      background: rgba(0, 0, 0, 0.5);
      border-radius: var(--border-radius-sm);
      max-height: 400px;
      overflow-y: auto;
      font-family: 'Courier New', monospace;
    }

    .database-content.active {
      display: block;
    }

    .database-item {
      padding: 0.8rem;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.9rem;
      color: var(--text-secondary);
    }

    .database-item-info strong {
      color: var(--accent);
    }

    .database-item-delete {
      color: var(--accent2);
      cursor: pointer;
      transition: var(--transition);
    }

    .database-item-delete:hover {
      transform: scale(1.2);
    }

    .footer {
      margin-top: 2rem;
      text-align: center;
      padding: 1.5rem;
      color: var(--text-secondary);
      font-size: 0.9rem;
    }

    .footer-locations {
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
      margin-top: 0.5rem;
    }

    .footer-locations span {
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    @media (max-width: 768px) {
      .navbar {
        flex-direction: column;
        gap: 1rem;
      }

      .hero {
        padding: 2rem;
      }

      .hero-content {
        flex-direction: column;
        align-items: flex-start;
      }

      .hero-text h1 {
        font-size: 2rem;
      }
    }
  </style>
</head>
<body>
  <!-- LOGIN PAGE -->
  <div class="auth-container" id="loginPage">
    <div class="auth-box">
      <div class="auth-header">
        <div class="auth-logo">
          <i class="fas fa-graduation-cap"></i>
        </div>
        <h1>PakTutor</h1>
        <p>Mathematics Hub · Login to Continue</p>
      </div>
      
      <form class="auth-form" id="loginForm">
        <div class="form-group">
          <label>Email Address</label>
          <i class="fas fa-envelope"></i>
          <input type="email" id="loginEmail" placeholder="Enter your email" required>
        </div>
        
        <div class="form-group">
          <label>Password</label>
          <i class="fas fa-lock"></i>
          <input type="password" id="loginPassword" placeholder="Enter your password" required>
        </div>
        
        <button type="submit" class="auth-btn">
          <i class="fas fa-sign-in-alt"></i> Login
        </button>
      </form>
      
      <div class="auth-links">
        <button class="auth-link-btn" onclick="showCreateAccount()">
          <i class="fas fa-user-plus"></i> Create New Account
        </button>
        <button class="auth-link-btn" onclick="showForgotPassword()">
          <i class="fas fa-key"></i> Forgot Password?
        </button>
      </div>
      
      <div class="contact-info">
        <p><i class="fas fa-phone"></i> Contact: <a href="tel:03314403596">0331-4403596</a></p>
        <p><i class="fas fa-envelope"></i> Email: <a href="mailto:support@paktutor.pk">support@paktutor.pk</a></p>
        <p><i class="fab fa-whatsapp"></i> WhatsApp: <a href="https://wa.me/923314403596" target="_blank">+92 331 4403596</a></p>
      </div>
    </div>
  </div>

  <!-- CREATE ACCOUNT PAGE -->
  <div class="auth-container" id="createAccountPage" style="display: none;">
    <div class="auth-box">
      <div class="auth-header">
        <div class="auth-logo" style="background: var(--gradient2); box-shadow: var(--shadow-neon2);">
          <i class="fas fa-user-plus"></i>
        </div>
        <h1 style="background: var(--gradient2); -webkit-background-clip: text; background-clip: text;">Create Account</h1>
        <p>Join PakTutor Mathematics Hub</p>
      </div>
      
      <form class="auth-form" id="createAccountForm">
        <div class="form-group">
          <label>Full Name</label>
          <i class="fas fa-user"></i>
          <input type="text" id="fullName" placeholder="Enter your full name" required>
        </div>
        
        <div class="form-group">
          <label>Email Address</label>
          <i class="fas fa-envelope"></i>
          <input type="email" id="createEmail" placeholder="Enter your email" required>
        </div>
        
        <div class="form-group">
          <label>Phone Number</label>
          <i class="fas fa-phone"></i>
          <input type="tel" id="phoneNumber" placeholder="0331-XXXXXXX" required>
        </div>
        
        <div class="form-group">
          <label>Password</label>
          <i class="fas fa-lock"></i>
          <input type="password" id="createPassword" placeholder="Create password (min 6 characters)" required>
        </div>
        
        <div class="form-group">
          <label>Confirm Password</label>
          <i class="fas fa-lock"></i>
          <input type="password" id="confirmPassword" placeholder="Confirm password" required>
        </div>
        
        <button type="submit" class="auth-btn" style="background: var(--gradient2); box-shadow: var(--shadow-neon2);">
          <i class="fas fa-check-circle"></i> Create Account
        </button>
      </form>
      
      <div id="createAccountMessage" class="success-message"></div>
      
      <div class="auth-links">
        <button class="auth-link-btn" onclick="showLogin()">
          <i class="fas fa-arrow-left"></i> Back to Login
        </button>
      </div>
      
      <div class="contact-info">
        <p><i class="fas fa-phone"></i> Need help? <a href="tel:03314403596">0331-4403596</a></p>
      </div>
    </div>
  </div>

  <!-- FORGOT PASSWORD PAGE -->
  <div class="auth-container" id="forgotPasswordPage" style="display: none;">
    <div class="auth-box">
      <div class="auth-header">
        <div class="auth-logo" style="background: var(--gradient3); box-shadow: var(--shadow-neon3);">
          <i class="fas fa-key"></i>
        </div>
        <h1 style="background: var(--gradient3); -webkit-background-clip: text; background-clip: text;">Forgot Password</h1>
        <p>We'll send you reset instructions</p>
      </div>
      
      <form class="auth-form" id="forgotPasswordForm">
        <div class="form-group">
          <label>Email Address</label>
          <i class="fas fa-envelope"></i>
          <input type="email" id="forgotEmail" placeholder="Enter your registered email" required>
        </div>
        
        <button type="submit" class="auth-btn" style="background: var(--gradient3); box-shadow: var(--shadow-neon3);">
          <i class="fas fa-paper-plane"></i> Send Reset Link
        </button>
      </form>
      
      <div id="forgotPasswordMessage" class="success-message"></div>
      
      <div class="auth-links">
        <button class="auth-link-btn" onclick="showLogin()">
          <i class="fas fa-arrow-left"></i> Back to Login
        </button>
      </div>
      
      <div class="contact-info">
        <p><i class="fas fa-phone"></i> Having trouble? <a href="tel:03314403596">0331-4403596</a></p>
        <p><i class="fab fa-whatsapp"></i> WhatsApp: <a href="https://wa.me/923314403596" target="_blank">+92 331 4403596</a></p>
      </div>
    </div>
  </div>

  <!-- MAIN APP -->
  <div class="main-container" id="mainApp">
    <div class="container">
      <nav class="navbar">
        <div class="nav-brand">
          <div class="nav-logo">
            <i class="fas fa-graduation-cap"></i>
          </div>
          <div>
            <div class="nav-title">PakTutor</div>
            <div class="nav-subtitle">Mathematics Hub · All Pakistan</div>
          </div>
        </div>
        <div class="nav-actions">
          <div class="user-info">
            <i class="fas fa-user-circle"></i>
            <span id="userEmail"></span>
          </div>
          <button class="nav-btn nav-btn-outline" onclick="logout()">
            <i class="fas fa-sign-out-alt"></i> Logout
          </button>
        </div>
      </nav>

      <section class="hero">
        <div class="hero-content">
          <div class="hero-avatar">
            <i class="fas fa-chalkboard-teacher"></i>
          </div>
          <div class="hero-text">
            <h1><i class="fas fa-star"></i> Miss. Maira Abrar</h1>
            <p>Lead Mathematics Instructor · 1000+ students across Pakistan</p>
            <div class="hero-badges">
              <span class="badge badge-primary">
                <i class="fas fa-rupee-sign"></i> 5K – 8K / subject
              </span>
              <span class="badge badge-success">
                <i class="fas fa-calendar-alt"></i> Monthly
              </span>
              <span class="badge badge-info">
                <i class="fas fa-globe-asia"></i> All Over Pakistan
              </span>
            </div>
          </div>
        </div>
      </section>

      <div class="filter-section">
        <div class="filter-tabs">
          <button class="filter-tab active" data-dept="all">
            <i class="fas fa-th-large"></i> All Subjects
          </button>
          <button class="filter-tab" data-dept="engineering">
            <i class="fas fa-microchip"></i> Engineering
          </button>
          <button class="filter-tab" data-dept="science">
            <i class="fas fa-flask"></i> Science
          </button>
          <button class="filter-tab" data-dept="commerce">
            <i class="fas fa-chart-line"></i> Commerce
          </button>
          <button class="filter-tab" data-dept="medicine">
            <i class="fas fa-heartbeat"></i> Medicine
          </button>
        </div>
      </div>

      <div class="subjects-grid" id="subjectsGrid"></div>

      <div class="live-banner">
        <div class="live-banner-left">
          <div class="live-indicator"></div>
          <div>
            <h3>LIVE Sessions</h3>
            <p>100% interactive · recorded backup</p>
          </div>
        </div>
        <div>
          <i class="fas fa-headset" style="color: var(--accent);"></i> 24/7 Support
        </div>
        <div>
          <i class="fas fa-phone" style="color: var(--accent3);"></i> 0331-4403596
        </div>
      </div>

      <div class="actions-grid">
        <button class="action-btn action-btn-primary" id="enrollBtn">
          <i class="fas fa-user-plus"></i> Enroll Now
        </button>
        <button class="action-btn action-btn-secondary" id="demoBtn">
          <i class="fas fa-play-circle"></i> Free Demo Class
        </button>
        <button class="action-btn action-btn-success" id="scheduleBtn">
          <i class="fas fa-clock"></i> Schedule
        </button>
        <button class="action-btn action-btn-info" id="contactBtn">
          <i class="fas fa-envelope"></i> Contact Us
        </button>
      </div>

      <div class="contact-section">
        <h2 style="color: var(--text-primary); margin-bottom: 1rem;">
          <i class="fas fa-address-book"></i> Contact Information
        </h2>
        <div class="contact-grid">
          <div class="contact-card">
            <i class="fas fa-phone"></i>
            <h4>Phone</h4>
            <a href="tel:03314403596">0331-4403596</a>
          </div>
          <div class="contact-card">
            <i class="fas fa-envelope"></i>
            <h4>Email</h4>
            <a href="mailto:support@paktutor.pk">support@paktutor.pk</a>
          </div>
          <div class="contact-card">
            <i class="fab fa-whatsapp"></i>
            <h4>WhatsApp</h4>
            <a href="https://wa.me/923314403596" target="_blank">+92 331 4403596</a>
          </div>
        </div>
      </div>

      <div class="database-section">
        <div class="database-header">
          <h2><i class="fas fa-database"></i> Enrollment Database</h2>
          <button class="database-toggle" id="dbToggle">
            <i class="fas fa-eye"></i> View Records
          </button>
        </div>
        <div class="database-content" id="databaseContent">
          <p style="color: #666;">No records yet.</p>
        </div>
      </div>

      <footer class="footer">
        <div class="footer-locations">
          <span><i class="fas fa-map-marker-alt"></i> Islamabad</span>
          <span><i class="fas fa-map-marker-alt"></i> Lahore</span>
          <span><i class="fas fa-map-marker-alt"></i> Karachi</span>
          <span><i class="fas fa-map-marker-alt"></i> Peshawar</span>
          <span><i class="fas fa-map-marker-alt"></i> Quetta</span>
        </div>
        <p style="margin-top: 0.5rem;">© 2024 PakTutor · All Rights Reserved</p>
      </footer>
    </div>
  </div>

  <script>
    (function() {
      // EmailJS configuration
      emailjs.init("YOUR_PUBLIC_KEY"); // Replace with your EmailJS public key
      
      const loginPage = document.getElementById('loginPage');
      const createAccountPage = document.getElementById('createAccountPage');
      const forgotPasswordPage = document.getElementById('forgotPasswordPage');
      const mainApp = document.getElementById('mainApp');
      
      window.showLogin = function() {
        loginPage.style.display = 'flex';
        createAccountPage.style.display = 'none';
        forgotPasswordPage.style.display = 'none';
        mainApp.style.display = 'none';
      };
      
      window.showCreateAccount = function() {
        loginPage.style.display = 'none';
        createAccountPage.style.display = 'flex';
        forgotPasswordPage.style.display = 'none';
        mainApp.style.display = 'none';
      };
      
      window.showForgotPassword = function() {
        loginPage.style.display = 'none';
        createAccountPage.style.display = 'none';
        forgotPasswordPage.style.display = 'flex';
        mainApp.style.display = 'none';
      };
      
      const USER_DB_KEY = 'paktutor_users_db';
      const VERIFICATION_DB_KEY = 'paktutor_verification_db';
      
      function getUsers() {
        return JSON.parse(localStorage.getItem(USER_DB_KEY) || '[]');
      }
      
      function addUser(user) {
        const users = getUsers();
        users.push(user);
        localStorage.setItem(USER_DB_KEY, JSON.stringify(users));
        return user;
      }
      
      function findUser(email) {
        const users = getUsers();
        return users.find(u => u.email === email);
      }
      
      function updateUser(email, updates) {
        const users = getUsers();
        const index = users.findIndex(u => u.email === email);
        if (index !== -1) {
          users[index] = { ...users[index], ...updates };
          localStorage.setItem(USER_DB_KEY, JSON.stringify(users));
          return users[index];
        }
        return null;
      }
      
      function getVerifications() {
        return JSON.parse(localStorage.getItem(VERIFICATION_DB_KEY) || '[]');
      }
      
      function addVerification(verification) {
        const verifications = getVerifications();
        verifications.push(verification);
        localStorage.setItem(VERIFICATION_DB_KEY, JSON.stringify(verifications));
        return verification;
      }
      
      function findVerification(email, code) {
        const verifications = getVerifications();
        return verifications.find(v => v.email === email && v.code === code);
      }
      
      function removeVerification(email) {
        let verifications = getVerifications();
        verifications = verifications.filter(v => v.email !== email);
        localStorage.setItem(VERIFICATION_DB_KEY, JSON.stringify(verifications));
      }
      
      function generateVerificationCode() {
        return Math.floor(100000 + Math.random() * 900000).toString();
      }
      
      function sendVerificationEmail(email, fullName, code) {
        const templateParams = {
          to_email: email,
          to_name: fullName,
          verification_code: code,
          subject: 'PakTutor - Verify Your Email Address'
        };
        
        return emailjs.send("YOUR_SERVICE_ID", "YOUR_VERIFICATION_TEMPLATE_ID", templateParams)
          .then(function(response) {
            return true;
          })
          .catch(function(error) {
            return false;
          });
      }
      
      function sendPasswordResetEmail(email, fullName, newPassword) {
        const templateParams = {
          to_email: email,
          to_name: fullName,
          new_password: newPassword,
          subject: 'PakTutor - Password Reset'
        };
        
        return emailjs.send("YOUR_SERVICE_ID", "YOUR_RESET_TEMPLATE_ID", templateParams)
          .then(function(response) {
            return true;
          })
          .catch(function(error) {
            return false;
          });
      }
      
      const loginForm = document.getElementById('loginForm');
      const userEmailDisplay = document.getElementById('userEmail');
      
      const savedUser = localStorage.getItem('paktutor_current_user');
      if (savedUser) {
        showMainApp(savedUser);
      }
      
      loginForm.addEventListener('submit', function(e) {
        e.preventDefault();
        const email = document.getElementById('loginEmail').value;
        const password = document.getElementById('loginPassword').value;
        
        const user = findUser(email);
        
        if (!user) {
          alert('Account not found! Please create an account first.');
          showCreateAccount();
          return;
        }
        
        if (!user.verified) {
          alert('Your email is not verified! Please check your email for verification code.');
          showVerificationPrompt(user);
          return;
        }
        
        if (user.password !== password) {
          alert('Incorrect password! Please try again.');
          return;
        }
        
        localStorage.setItem('paktutor_current_user', email);
        showMainApp(email);
      });
      
      function showMainApp(email) {
        loginPage.style.display = 'none';
        createAccountPage.style.display = 'none';
        forgotPasswordPage.style.display = 'none';
        mainApp.style.display = 'block';
        userEmailDisplay.textContent = email;
        renderSubjects('all');
      }
      
      window.logout = function() {
        localStorage.removeItem('paktutor_current_user');
        showLogin();
        document.getElementById('loginEmail').value = '';
        document.getElementById('loginPassword').value = '';
      };
      
      function showVerificationPrompt(user) {
        const code = prompt(`Please enter the 6-digit verification code sent to ${user.email}:`);
        if (code) {
          verifyAccount(user.email, code);
        }
      }
      
      function verifyAccount(email, code) {
        const verification = findVerification(email, code);
        
        if (verification) {
          updateUser(email, { verified: true });
          removeVerification(email);
          alert('✅ Email verified successfully! You can now login.');
          showLogin();
          document.getElementById('loginEmail').value = email;
        } else {
          alert('Invalid verification code! Please try again.');
        }
      }
      
      const createAccountForm = document.getElementById('createAccountForm');
      const createAccountMessage = document.getElementById('createAccountMessage');
      
      createAccountForm.addEventListener('submit', async function(e) {
        e.preventDefault();
        const fullName = document.getElementById('fullName').value;
        const email = document.getElementById('createEmail').value;
        const phone = document.getElementById('phoneNumber').value;
        const password = document.getElementById('createPassword').value;
        const confirmPassword = document.getElementById('confirmPassword').value;
        
        if (password !== confirmPassword) {
          alert('Passwords do not match!');
          return;
        }
        
        if (password.length < 6) {
          alert('Password must be at least 6 characters!');
          return;
        }
        
        if (findUser(email)) {
          alert('Account with this email already exists! Please login.');
          showLogin();
          return;
        }
        
        const verificationCode = generateVerificationCode();
        
        const newUser = {
          fullName: fullName,
          email: email,
          phone: phone,
          password: password,
          verified: false,
          createdAt: new Date().toISOString()
        };
        
        addUser(newUser);
        addVerification({
          email: email,
          code: verificationCode,
          createdAt: new Date().toISOString()
        });
        
        createAccountMessage.textContent = '📧 Sending verification email...';
        createAccountMessage.classList.add('show');
        
        const emailSent = await sendVerificationEmail(email, fullName, verificationCode);
        
        if (emailSent) {
          createAccountMessage.textContent = `✅ Verification code sent to ${email}!`;
        } else {
          createAccountMessage.innerHTML = `
            <strong>Demo Mode:</strong><br>
            Your verification code is: <strong style="color: var(--accent4); font-size: 1.5rem;">${verificationCode}</strong><br>
            <small>Configure EmailJS to send real emails.</small>
          `;
        }
        
        createAccountForm.reset();
        
        setTimeout(() => {
          createAccountMessage.classList.remove('show');
          showLogin();
          document.getElementById('loginEmail').value = email;
          alert('Please check your email for verification code.');
        }, 5000);
      });
      
      const forgotPasswordForm = document.getElementById('forgotPasswordForm');
      const forgotPasswordMessage = document.getElementById('forgotPasswordMessage');
      
      forgotPasswordForm.addEventListener('submit', async function(e) {
        e.preventDefault();
        const email = document.getElementById('forgotEmail').value;
        
        const user = findUser(email);
        
        if (!user) {
          alert('No account found with this email. Please create an account.');
          showCreateAccount();
          return;
        }
        
        const tempPassword = generateVerificationCode();
        updateUser(email, { password: tempPassword, verified: true });
        
        forgotPasswordMessage.textContent = '📧 Sending password reset email...';
        forgotPasswordMessage.classList.add('show');
        
        const emailSent = await sendPasswordResetEmail(email, user.fullName, tempPassword);
        
        if (emailSent) {
          forgotPasswordMessage.innerHTML = `✅ Password reset instructions sent to ${email}!`;
        } else {
          forgotPasswordMessage.innerHTML = `
            <strong>Demo Mode:</strong><br>
            Your temporary password is: <strong style="color: var(--accent4); font-size: 1.5rem;">${tempPassword}</strong><br>
            <small>Configure EmailJS to send real emails.</small>
          `;
        }
        
        forgotPasswordForm.reset();
        
        setTimeout(() => {
          forgotPasswordMessage.classList.remove('show');
          showLogin();
          document.getElementById('loginEmail').value = email;
        }, 5000);
      });
      
      const DB_KEY = 'paktutor_enrollments_db_v7';
      
      function getEnrollments() {
        return JSON.parse(localStorage.getItem(DB_KEY) || '[]');
      }
      
      function addEnrollment(record) {
        const db = getEnrollments();
        record.id = Date.now() + Math.floor(Math.random() * 1000);
        record.timestamp = new Date().toLocaleString();
        record.user = localStorage.getItem('paktutor_current_user') || 'anonymous';
        db.push(record);
        localStorage.setItem(DB_KEY, JSON.stringify(db));
        return record;
      }
      
      function removeEnrollment(id) {
        let db = getEnrollments();
        db = db.filter(r => r.id !== id);
        localStorage.setItem(DB_KEY, JSON.stringify(db));
      }
      
      const subjects = [
        { name: "Calculus I", dept: "engineering", icon: "fa-calculator", fee: "5,000" },
        { name: "Linear Algebra", dept: "engineering", icon: "fa-vector-square", fee: "6,500" },
        { name: "Discrete Math", dept: "science", icon: "fa-shapes", fee: "5,800" },
        { name: "Statistics", dept: "commerce", icon: "fa-chart-bar", fee: "5,200" },
        { name: "Differential Eq.", dept: "engineering", icon: "fa-wave-square", fee: "7,200" },
        { name: "Abstract Algebra", dept: "science", icon: "fa-ring", fee: "6,900" },
        { name: "Business Math", dept: "commerce", icon: "fa-money-bill-wave", fee: "5,000" },
        { name: "Biostatistics", dept: "medicine", icon: "fa-heart", fee: "7,500" },
        { name: "Geometry", dept: "science", icon: "fa-draw-polygon", fee: "5,500" },
        { name: "Numerical Methods", dept: "engineering", icon: "fa-robot", fee: "7,800" },
      ];
      
      const grid = document.getElementById('subjectsGrid');
      const filterTabs = document.querySelectorAll('.filter-tab');
      const dbToggle = document.getElementById('dbToggle');
      const databaseContent = document.getElementById('databaseContent');
      
      function renderSubjects(dept = 'all') {
        grid.innerHTML = '';
        const filtered = dept === 'all' ? subjects : subjects.filter(s => s.dept === dept);
        
        filtered.forEach(sub => {
          const card = document.createElement('div');
          card.className = 'subject-card';
          card.innerHTML = `
            <div class="subject-card-header">
              <div class="subject-card-icon">
                <i class="fas ${sub.icon}"></i>
              </div>
              <div class="subject-card-title">
                <h3>${sub.name}</h3>
                <div class="subject-card-dept">
                  <i class="fas fa-building"></i> ${sub.dept.charAt(0).toUpperCase() + sub.dept.slice(1)}
                </div>
              </div>
            </div>
            <div class="subject-card-fee">
              <span>Monthly Fee</span>
              <strong>PKR ${sub.fee}</strong>
            </div>
            <button class="subject-card-btn" data-subject="${sub.name}" data-dept="${sub.dept}" data-fee="${sub.fee}">
              <i class="fas fa-graduation-cap"></i> Enroll Now
            </button>
          `;
          grid.appendChild(card);
        });
        
        document.querySelectorAll('.subject-card-btn').forEach(btn => {
          btn.addEventListener('click', function() {
            const subject = this.getAttribute('data-subject');
            const dept = this.getAttribute('data-dept');
            const fee = this.getAttribute('data-fee');
            
            addEnrollment({
              subject: subject,
              department: dept,
              fee: fee,
              instructor: 'Miss. Maira Abrar',
              status: 'Pending'
            });
            
            alert(`✅ Enrollment Successful!\n\nSubject: ${subject}\nFee: PKR ${fee}/month\n\nContact: 0331-4403596`);
            updateDatabase();
          });
        });
      }
      
      function updateDatabase() {
        const db = getEnrollments();
        if (db.length === 0) {
          databaseContent.innerHTML = '<p style="color: #666;">No records yet.</p>';
          return;
        }
        
        let html = '';
        db.slice().reverse().forEach(record => {
          html += `
            <div class="database-item">
              <div class="database-item-info">
                <strong>${record.subject}</strong>
                <span>${record.department}</span>
                <span>PKR ${record.fee}</span>
                <span style="color: #ffd700;">${record.status}</span>
                <small style="color: #666;">(${record.user})</small>
              </div>
              <div class="database-item-delete" onclick="window.removeRecord(${record.id})">
                <i class="fas fa-trash-alt"></i>
              </div>
            </div>
          `;
        });
        databaseContent.innerHTML = html;
      }
      
      window.removeRecord = function(id) {
        if (confirm('Delete this record?')) {
          removeEnrollment(id);
          updateDatabase();
        }
      };
      
      filterTabs.forEach(tab => {
        tab.addEventListener('click', function() {
          filterTabs.forEach(t => t.classList.remove('active'));
          this.classList.add('active');
          renderSubjects(this.getAttribute('data-dept'));
        });
      });
      
      document.getElementById('enrollBtn').addEventListener('click', function() {
        addEnrollment({
          subject: 'General Enrollment',
          department: 'All',
          fee: '5K-8K',
          instructor: 'Miss. Maira Abrar',
          status: 'Interest'
        });
        alert('📚 Enrollment request saved! Call 0331-4403596 for details.');
        updateDatabase();
      });
      
      document.getElementById('demoBtn').addEventListener('click', function() {
        addEnrollment({
          subject: 'Demo Class Request',
          department: 'Any',
          fee: 'Free',
          instructor: 'Miss. Maira Abrar',
          status: 'Demo'
        });
        alert('🎥 Free demo class scheduled! Contact: 0331-4403596');
        updateDatabase();
      });
      
      document.getElementById('scheduleBtn').addEventListener('click', function() {
        addEnrollment({
          subject: 'Schedule Request',
          department: 'Flexible',
          fee: '—',
          instructor: 'Miss. Maira Abrar',
          status: 'Scheduling'
        });
        alert('📅 Schedule request saved! Contact: 0331-4403596');
        updateDatabase();
      });
      
      document.getElementById('contactBtn').addEventListener('click', function() {
        window.location.href = 'tel:03314403596';
      });
      
      dbToggle.addEventListener('click', function() {
        const isActive = databaseContent.classList.toggle('active');
        if (isActive) {
          dbToggle.innerHTML = '<i class="fas fa-eye-slash"></i> Hide Records';
          updateDatabase();
        } else {
          dbToggle.innerHTML = '<i class="fas fa-eye"></i> View Records';
        }
      });
      
      console.log('✅ PakTutor Premium Edition loaded successfully!');
    })();
  </script>
</body>
</html>
