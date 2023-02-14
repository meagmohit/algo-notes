---
layout: default
title: Home
nav_order: 1
description: "Landing Page"
permalink: /
---

<button class="btn js-toggle-dark-mode">Switch to Dark Theme</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Switch to Dark Theme';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Return to Light Theme';
  }
});
</script>

# Data Structures and Algorithms (in Python)

These notes are written in README format, and meant for quick brush-up before the interviews.
