---
layout: default
---

<div class="profile-page">
 

  <div class="profile-content">
    <div class="profile-header">
      <div class="text-content">
        <h1 class="name">{{ site.author.name }}</h1>
        <h2 class="title">Senior ML Engineer</h2>
        <div class="button-group">
          <a href="https://calendly.com/murtazaarif2k16/30min" target="_blank" class="cta-button">
            <span class="button-content">
              <i class="fas fa-calendar-alt"></i>
              <span class="button-text">Get in Touch</span>
            </span>
          </a>
          <a href="/assets/resume.pdf" target="_blank" class="cta-button download-btn">
            <span class="button-content">
              <i class="fas fa-file-download"></i>
              <span class="button-text">Download CV</span>
            </span>
          </a>
        </div>
      </div>
      <div class="profile-image">
        <img src="https://i.ibb.co/KGF2CLs/murtaza.jpg" alt="{{ site.author.name }}" />
      </div>
    </div>

    <div class="stats">
      <div class="stat-item">
        <h3>8+</h3>
        <p>Years<br>experience</p>
      </div>
      
      <div class="stat-item">
        <h3>30+</h3>
        <p>ML Models<br>Deployed</p>
      </div>
      
      <div class="stat-item">
        <h3>03</h3>
        <p>AWS<br>Certifications</p>
      </div>
      
      <div class="stat-item">
        <h3>7+</h3>
        <p>LLM<br>Projects</p>
      </div>
    </div>
  </div>
</div>

<style>
.profile-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.social-links {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.social-icon {
  width: 45px;
  height: 45px;
  border: 2px solid var(--text-color);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-color);
  font-size: 1.2rem;
  transition: all 0.3s ease;
}

.social-icon:hover {
  background-color: var(--text-color);
  color: var(--bg-color);
  transform: translateY(-3px);
}

.profile-content {
  text-align: center;
  width: 100%;
}

.profile-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 3rem;
  gap: 2rem;
}

.text-content {
  flex: 1;
  text-align: left;
}

.profile-image {
  flex: 1;
  max-width: 300px;
}

.profile-image img {
  width: 100%;
  height: auto;
  border-radius: 20px;
  transition: transform 0.3s ease;
}

.profile-image img:hover {
  transform: translateY(-5px);
}

.name {
  font-size: 3.5rem;
  font-weight: 500;
  margin-bottom: 0.5rem;
  color: var(--text-color);
}

.title {
  font-size: 1.8rem;
  color: var(--secondary);
  font-weight: 400;
  margin-bottom: 2rem;
}

.button-group {
  display: flex;
  gap: 1.5rem;
  margin-top: 1.5rem;
}

.cta-button {
  display: inline-block;
  padding: 0.9rem 2.2rem;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  position: relative;
  color: var(--text-color);
  background: var(--bg-color);
  border: none;
  z-index: 1;
  border-radius: 50px;
}

.cta-button::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 50px;
  padding: 3px;
  background: linear-gradient(120deg, #00bcd4 0%, #3f51b5 50%, #00bcd4 100%);
  -webkit-mask: 
    linear-gradient(#fff 0 0) content-box, 
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}

.button-content {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.8rem;
  position: relative;
}

.button-text {
  font-size: 1rem;
  letter-spacing: 0.5px;
}

.cta-button i {
  font-size: 1.1rem;
  transition: transform 0.4s ease;
}

.cta-button:hover {
  transform: translateY(-2px);
}

.cta-button:hover::before {
  background: linear-gradient(120deg, #3f51b5 0%, #00bcd4 50%, #3f51b5 100%);
}

.cta-button:hover i {
  transform: scale(1.1);
}

.download-btn::before {
  background: linear-gradient(120deg, #4caf50 0%, #8bc34a 50%, #4caf50 100%);
}

.download-btn:hover::before {
  background: linear-gradient(120deg, #8bc34a 0%, #4caf50 50%, #8bc34a 100%);
}

.stats {
  display: flex;
  justify-content: center;
  gap: 4rem;
  flex-wrap: wrap;
  margin-top: 4rem;
  padding: 0 2rem;
}

.stat-item {
  text-align: center;
}

.stat-item h3 {
  font-size: 2.5rem;
  font-weight: 500;
  margin-bottom: 0.5rem;
  color: var(--text-color);
}

.stat-item p {
  font-size: 1.1rem;
  color: var(--secondary);
  line-height: 1.4;
}

@media (max-width: 968px) {
  .profile-header {
    flex-direction: column-reverse;
    text-align: center;
  }
  
  .text-content {
    text-align: center;
  }
  
  .profile-image {
    max-width: 300px;
  }
  
  .stats {
    margin-top: 3rem;
  }
}

@media (max-width: 768px) {
  .name {
    font-size: 2.5rem;
  }
  
  .title {
    font-size: 1.4rem;
  }
  
  .stats {
    gap: 2rem;
    margin-top: 2rem;
  }
  
  .stat-item h3 {
    font-size: 2rem;
  }
  
  .stat-item p {
    font-size: 1rem;
  }
  
  .button-group {
    flex-direction: column;
    align-items: stretch;
    gap: 1rem;
  }
  
  .cta-button {
    text-align: center;
    padding: 0.8rem 1.8rem;
  }
  
  .button-content {
    justify-content: center;
  }
}

@media (prefers-color-scheme: dark) {
  .cta-button {
    color: var(--text-color);
    background: var(--bg-color);
  }
}
</style>
