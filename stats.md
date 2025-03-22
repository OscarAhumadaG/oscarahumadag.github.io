---
layout: default
title: ""
permalink: /stats/
---

<!-- Font Awesome CDN -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  .stats-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 30px;
    margin-top: 40px;
  }

  .stat-box {
    background: #fff;
    border-radius: 16px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    padding: 25px;
    text-align: center;
    width: 180px;
    transition: transform 0.3s ease;
    position: relative;
  }

  .stat-box:hover {
    transform: scale(1.05);
  }

  .stat-icon {
    font-size: 40px;
    margin-bottom: 10px;
    color: #0077b5;
  }

  .stat-number {
    font-size: 24px;
    font-weight: bold;
    color: #333;
  }

  .stat-label {
    font-size: 14px;
    color: #555;
    margin-top: 5px;
  }

  .tooltip {
    visibility: hidden;
    opacity: 0;
    transition: opacity 0.3s;
    position: absolute;
    bottom: 100%;
    left: 50%;
    transform: translateX(-50%);
    background-color: #333;
    color: #fff;
    padding: 5px 8px;
    border-radius: 5px;
    font-size: 12px;
    white-space: nowrap;
    z-index: 100;
    margin-bottom: 8px;
  }

  .stat-box:hover .tooltip,
  .stat-box:focus .tooltip,
  .stat-box.touch-active .tooltip {
    visibility: visible;
    opacity: 1;
  }
</style>

<!-- General Stats -->
<div align="center">
  <h2>GENERAL STATS</h2>
</div>

<div class="stats-container">
  <div class="stat-box" data-tooltip="Approximately X years">
    <div class="stat-icon"><i class="fas fa-user"></i></div>
    <div class="stat-number" id="ageDays">...</div>
    <div class="stat-label">Days Old</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="Since December 7, 2013: ~X years">
    <div class="stat-icon"><i class="fas fa-ring"></i></div>
    <div class="stat-number" id="marriedDays">...</div>
    <div class="stat-label">Days Married</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="Mateo and Ethan">
    <div class="stat-icon"><i class="fas fa-child"></i></div>
    <div class="stat-number">2</div>
    <div class="stat-label">Children</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="Spanish, English, French">
    <div class="stat-icon"><i class="fas fa-language"></i></div>
    <div class="stat-number">3</div>
    <div class="stat-label">Languages</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="Colombia and Canada">
    <div class="stat-icon"><i class="fas fa-home"></i></div>
    <div class="stat-number">2</div>
    <div class="stat-label">Countries Lived</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="Colombia, Canada, USA">
    <div class="stat-icon"><i class="fas fa-plane-departure"></i></div>
    <div class="stat-number">3</div>
    <div class="stat-label">Countries Visited</div>
    <div class="tooltip"></div>
  </div>
</div>

<!-- Hobbies & Interests -->
<div align="center" style="margin-top: 60px;">
  <h2>HOBBIES & INTERESTS</h2>
</div>

<div class="stats-container">
  <div class="stat-box" data-tooltip="I use Canva for my designs">
    <div class="stat-icon"><i class="fas fa-pen-nib"></i></div>
    <div class="stat-label">Graphic Design</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="Fan of Junior de Barranquilla & Real Madrid">
    <div class="stat-icon"><i class="fas fa-futbol"></i></div>
    <div class="stat-label">Soccer</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="I draw using Procreate">
    <div class="stat-icon"><i class="fas fa-pencil-alt"></i></div>
    <div class="stat-label">Drawing</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="FIFA is my favorite">
    <div class="stat-icon"><i class="fas fa-gamepad"></i></div>
    <div class="stat-label">Video Games</div>
    <div class="tooltip"></div>
  </div>
  <div class="stat-box" data-tooltip="I enjoy all music genres">
    <div class="stat-icon"><i class="fas fa-headphones-alt"></i></div>
    <div class="stat-label">Music</div>
    <div class="tooltip"></div>
  </div>
</div>

<script>
  function calculateDaysSince(dateString) {
    const today = new Date();
    const pastDate = new Date(dateString);
    const timeDiff = today - pastDate;
    return Math.floor(timeDiff / (1000 * 60 * 60 * 24));
  }

  function calculateYearsFromDays(days) {
    return (days / 365.25).toFixed(1);
  }

  document.addEventListener('DOMContentLoaded', function () {
    const ageDays = calculateDaysSince('1988-09-26');
    const marriedDays = calculateDaysSince('2013-12-07');

    document.getElementById('ageDays').textContent = `${ageDays} days`;
    document.getElementById('ageDays').parentElement.querySelector('.tooltip').textContent = `Approximately ${calculateYearsFromDays(ageDays)} years`;

    document.getElementById('marriedDays').textContent = `${marriedDays} days`;
    document.getElementById('marriedDays').parentElement.querySelector('.tooltip').textContent = `Since December 7, 2013: ~${calculateYearsFromDays(marriedDays)} years`;

    // Mobile touch tooltips
    document.querySelectorAll('.stat-box').forEach(box => {
      box.addEventListener('touchstart', function (e) {
        // Remove class from others
        document.querySelectorAll('.stat-box').forEach(b => b.classList.remove('touch-active'));
        this.classList.add('touch-active');
      });
    });

    document.addEventListener('touchstart', function (e) {
      if (!e.target.closest('.stat-box')) {
        document.querySelectorAll('.stat-box').forEach(b => b.classList.remove('touch-active'));
      }
    });
  });
</script>
