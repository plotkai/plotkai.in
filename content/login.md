---
title: "Login"
url: "/login/"
description: "Sign in to your Plotkai Interactive client dashboard."
---

<div class="login-container" id="login-gate">
  <div id="check-loader" style="text-align: center;">
    <div class="spinner"></div>
    <p style="margin-top: 15px; color: #666; font-size: 14px;">Connecting to Plotkai...</p>
    <div id="manual-override" style="display: none; margin-top: 15px; animation: fadeInUp 0.4s ease-out;">
      <p style="font-size: 12px; color: #999; margin-bottom: 8px;">Taking longer than usual?</p>
      <a href="https://home.plotkai.in" style="color: #7ed857; font-size: 13px; font-weight: 700; text-decoration: none; border: 1px solid #7ed857; padding: 5px 12px; border-radius: 6px;">Try Dashboard Anyway →</a>
    </div>
  </div>
  <div class="login-card sleep-card" id="sleep-message" style="display: none;">
    <div class="sleep-icon">🌙</div>
    <h2 class="sleep-title">Our Servers Are Asleep</h2>
    <p class="sleep-subtitle">The dashboard is available between <strong>9:00 AM — 6:00 PM IST</strong></p>
    <div class="sleep-divider"></div>
    <p class="sleep-body">
      We believe in sustainable work — and so do our servers.<br>
      Come back during business hours and we'll be ready for you.
    </p>
    <div class="sleep-clock" id="sleep-clock"></div>
    <p class="sleep-hint">Need urgent help? Reach us at <a href="mailto:contact@plotkai.in">contact@plotkai.in</a></p>
  </div>
</div>

<style>
.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 55vh;
  padding: 40px 20px;
}

.sleep-card {
  width: 100%;
  max-width: 480px;
  border: 1.5px solid #e8e8e8;
  border-radius: 16px;
  padding: 50px 40px;
  background: white;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.06);
  text-align: center;
  animation: fadeInUp 0.6s ease-out;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.sleep-icon {
  font-size: 64px;
  margin-bottom: 10px;
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

.sleep-title {
  font-family: 'PT Serif Caption', serif !important;
  font-size: 28px !important;
  color: #161616 !important;
  margin: 10px 0 8px 0 !important;
}

.sleep-subtitle {
  font-size: 15px !important;
  color: #666 !important;
  margin: 0 0 20px 0 !important;
}

.sleep-subtitle strong {
  color: #7ed857;
  font-weight: 900;
}

.sleep-divider {
  width: 60px;
  height: 3px;
  background: linear-gradient(90deg, #7ed857, #5cb83c);
  border-radius: 3px;
  margin: 0 auto 20px auto;
}

.sleep-body {
  font-size: 16px !important;
  line-height: 1.7 !important;
  color: #555 !important;
  margin: 0 0 25px 0 !important;
}

.sleep-clock {
  font-family: 'Courier New', monospace;
  font-size: 22px;
  font-weight: bold;
  color: #161616;
  background: #f5f5f5;
  display: inline-block;
  padding: 10px 22px;
  border-radius: 8px;
  margin-bottom: 20px;
  letter-spacing: 2px;
  border: 1px solid #e0e0e0;
}

.sleep-hint {
  font-size: 13px !important;
  color: #999 !important;
  margin: 0 !important;
}

.sleep-hint a {
  color: #7ed857 !important;
  font-weight: 700;
  border: none !important;
}

.sleep-hint a:hover {
  background: none !important;
  opacity: 0.8;
}

.spinner {
  width: 40px;
  height: 40px;
  border: 3px solid #f3f3f3;
  border-top: 3px solid #7ed857;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin: 0 auto;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>

<script>
(function() {
  var sleepMessage = document.getElementById('sleep-message');
  var loader = document.getElementById('check-loader');
  var override = document.getElementById('manual-override');

  function updateClock() {
    var now = new Date();
    var utc = now.getTime() + now.getTimezoneOffset() * 60000;
    var ist = new Date(utc + 5.5 * 3600000);
    var h = ist.getHours().toString().padStart(2, '0');
    var m = ist.getMinutes().toString().padStart(2, '0');
    var s = ist.getSeconds().toString().padStart(2, '0');
    var el = document.getElementById('sleep-clock');
    if (el) el.textContent = h + ':' + m + ':' + s + ' IST';
  }

  function showSleep() {
    if (loader) loader.style.display = 'none';
    if (sleepMessage) {
      sleepMessage.style.display = 'block';
      updateClock();
      setInterval(updateClock, 1000);
    }
  }

  function verifyWithImage(testUrl) {
    // We use the "Image Trick" with a known Authentik static asset.
    // Cloudflare 530/1033 errors return HTML/Text, which triggers img.onerror.
    var img = new Image();
    var timeout = setTimeout(function() {
      console.log('Image check timed out. Showing manual override.');
      if (override) override.style.display = 'block';
    }, 4000);

    img.onload = function() {
      clearTimeout(timeout);
      console.log('Authentik asset verified. Redirecting...');
      window.location.href = 'https://home.plotkai.in';
    };

    img.onerror = function() {
      clearTimeout(timeout);
      console.log('Asset load failed. This usually means Cloudflare 530/1033.');
      showSleep();
    };

    var assetPath = '/static/dist/assets/icons/icon_left_brand.svg';
    img.src = testUrl.replace(/\/$/, '') + assetPath + '?v=' + Date.now();
  }

  async function checkReachability() {
    var testUrl = 'https://auth.plotkai.in';

    // Show override link if it takes too long
    setTimeout(function() {
      if (loader && loader.style.display !== 'none' && override) {
        override.style.display = 'block';
      }
    }, 3500);

    try {
      var controller = new AbortController();
      var timeout = setTimeout(function() { controller.abort(); }, 7000);
      
      // 1. Try a standard fetch to detect specific status codes if CORS is allowed
      var response = await fetch(testUrl, { 
        mode: 'cors', 
        signal: controller.signal,
        cache: 'no-store' 
      });
      
      var text = await response.text();
      clearTimeout(timeout);

      if (response.status === 530 || text.includes('1033')) {
        showSleep();
      } else {
        window.location.href = 'https://home.plotkai.in';
      }
    } catch (err) {
      clearTimeout(timeout);
      // 2. If fetch fails (CORS block or network error), fallback to Image trick for production
      verifyWithImage(testUrl);
    }
  }

  checkReachability();
})();
</script>
