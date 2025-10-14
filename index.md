---
layout: default
title: "Cybersecurity Projects"
---

# Cybersecurity Projects Portfolio

Welcome! This is a collection of technical security projects exploring vulnerabilities, exploitation techniques, and defensive research.

---

## Projects

<ul>
  {% assign sorted_projects = site.projects | sort: 'date' | reverse %}
  {% for project in sorted_projects %}
    <li>
      <a href="{{ project.url | relative_url }}"><strong>{{ project.title }}</strong></a><br>
      {% if project.summary %}
        <small>{{ project.summary }}</small>
      {% endif %}
    </li>
  {% endfor %}
</ul>

---
  <p>© {{ site.time | date: "%Y" }} — Hands‑on cybersecurity projects.</p>

  <p>
    <a href="https://github.com/miamaco" target="_blank" rel="noopener">GitHub</a>
    · <a href="/projects/">Projects</a>
    · <a href="/about/">About</a>
    · <a href="">Contact</a>
  </p>

  <p class="small">
    Last updated: {{ site.time | date: "%Y-%m-%d" }}
  </p>

  <p class="disclaimer small">
    <strong>Disclaimer:</strong> Disclaimer: The code and analyses on this site are provided for educational and defensive research only. Do not use these materials to perform unauthorized testing or attacks. The author is not responsible for misuse.
  </p>
---