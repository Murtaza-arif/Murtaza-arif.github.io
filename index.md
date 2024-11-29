---
layout: default
---

<div class="profile-page">
 

  <div class="profile-content">
    <div class="profile-header">
      <div class="text-content">
        <h1 class="name">{{ site.author.name }}</h1>
        <h2 class="title">Senior ML Engineer</h2>
         <a href="https://calendly.com/murtazaarif2k16/30min" target="_blank" class="cta-button">Get in Touch</a>
      </div>
      <div class="profile-image">
        <img src="https://i.ibb.co/KGF2CLs/murtaza.jpg" alt="{{ site.author.name }}" />
      </div>
    </div>
<br>
<br>
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
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
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

.cta-button {
  display: inline-block;
  padding: 0.8rem 2rem;
  background-color: var(--text-color);
  color: var(--bg-color);
  border-radius: 50px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  border: 2px solid #00bcd4;
  position: relative;
  background: linear-gradient(var(--text-color), var(--text-color)) padding-box,
              linear-gradient(45deg, #00bcd4, #2196f3) border-box;
}

.cta-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  background: linear-gradient(var(--text-color), var(--text-color)) padding-box,
              linear-gradient(45deg, #2196f3, #00bcd4) border-box;
}

.stats {
  display: flex;
  justify-content: center;
  gap: 4rem;
  flex-wrap: wrap;
  margin-top: 2rem;
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
  }
  
  .stat-item h3 {
    font-size: 2rem;
  }
  
  .stat-item p {
    font-size: 1rem;
  }
}

@media (prefers-color-scheme: dark) {
  .social-icon {
    border-color: var(--text-color);
    color: var(--text-color);
  }
  
  .social-icon:hover {
    background-color: var(--text-color);
    color: var(--bg-color);
  }
  
  .cta-button {
    background: linear-gradient(var(--text-color), var(--text-color)) padding-box,
                linear-gradient(45deg, #00bcd4, #2196f3) border-box;
  }
  
  .cta-button:hover {
    background: linear-gradient(var(--text-color), var(--text-color)) padding-box,
                linear-gradient(45deg, #2196f3, #00bcd4) border-box;
  }
  
  .profile-image img {
    box-shadow: 0 10px 30px rgba(255,255,255,0.1);
  }
}
</style>
