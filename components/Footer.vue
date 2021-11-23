<script setup></script>

<template>
  <div class="footer-wrapper">
    <div class="footer-grid-wrapper">
      <nav>
        <h2 class="footer-nav-heading">Discover Content</h2>
        <ul class="footer-nav-list">
          <li>
            <a href="/pol">Politics</a>
          </li>
          <li>
            <a href="/wrl">World</a>
          </li>
          <li>
            <a href="/fin">Financial</a>
          </li>
          <li>
            <a href="/spo">Sports and Entertainment</a>
          </li>
          <li>
            <a href="/oped">Opinion and Editorial</a>
          </li>
        </ul>
      </nav>
      <nav>
        <h2 class="footer-nav-heading">Regional Websites</h2>
        <ul class="footer-nav-list">
          <li>
            <a href="/us">New Grid United States</a>
          </li>
          <li>
            <a href="/eu">New Grid Europe</a>
          </li>
          <li>
            <a href="/asia">New Grid Asia</a>
          </li>
          <li>
            <a href="/mars">New Grid Mars and Beyond</a>
          </li>
          <li>
            <a href="/au">New Grid Australia</a>
          </li>
        </ul>
      </nav>
      <nav>
        <h2 class="footer-nav-heading">Careers</h2>
        <ul class="footer-nav-list">
          <li>
            <a href="/pos">Open Positions</a>
          </li>
          <li>
            <a href="/team">Meet the team</a>
          </li>
          <li>
            <a href="/culture">Company Culture</a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<style>
.footer-wrapper {
  width: 100%;
  color: white;
  background: hsl(24deg 6% 16%);
}

.footer-grid-wrapper {
  display: grid;
  grid-template-columns: repeat(3, minmax(150px, 1fr));
  /* grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); */
  /* grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); */
  text-align: left;
  gap: 32px;
  padding: 24px 32px 32px 32px;
}

.footer-nav-heading {
  font-size: 16px !important;
  font-weight: bold;
  color: hsl(35deg 8% 80%);
  margin-bottom: 8px;
}

.footer-nav-list {
  display: flex;
  flex-direction: column;
  gap: 4px;

  list-style: none !important;
}

.footer-nav-list li {
  margin: 0 !important;
  padding: 0 !important;
  font-size: 12px;
}
</style>
