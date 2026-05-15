---
title: "Login"
url: "/login/"
description: "Sign in to your Plotkai Interactive client dashboard."
---

<div class="login-container" id="login-gate">
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
</style>

<script>
(function() {
  // Get current time in IST (UTC+5:30)
  function getISTHour() {
    var now = new Date();
    var utc = now.getTime() + now.getTimezoneOffset() * 60000;
    var ist = new Date(utc + 5.5 * 3600000);
    return { hour: ist.getHours(), date: ist };
  }

  function updateClock() {
    var ist = getISTHour().date;
    var h = ist.getHours().toString().padStart(2, '0');
    var m = ist.getMinutes().toString().padStart(2, '0');
    var s = ist.getSeconds().toString().padStart(2, '0');
    var el = document.getElementById('sleep-clock');
    if (el) el.textContent = h + ':' + m + ':' + s + ' IST';
  }

  var istHour = getISTHour().hour;

  if (istHour >= 9 && istHour < 18) {
    // Business hours — redirect to dashboard
    window.location.href = 'https://home.plotkai.in';
  } else {
    // Outside business hours — show sleep message
    var msg = document.getElementById('sleep-message');
    if (msg) msg.style.display = 'block';
    updateClock();
    setInterval(updateClock, 1000);
  }
})();
</script>
