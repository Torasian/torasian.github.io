<template>
  <div class="about">
    <div class="container">
      <h1>About Me</h1>
      <div class="content">
        <div class="bio">
          <h2>William Hawken</h2>
          <p class="title">Multidisciplinary Designer & Front End Developer</p>
          <p class="description">
            I'm a passionate designer and developer with a keen eye for detail and a love for creating
            beautiful, functional digital experiences. My approach combines technical expertise with
            creative problem-solving to deliver solutions that not only look great but also provide
            exceptional user experiences.
          </p>
        </div>
        
        <div class="skills">
          <h3>Skills & Expertise</h3>
          <div class="skill-categories">
            <div class="category">
              <h4>Design</h4>
              <ul>
                <li>UI/UX Design</li>
                <li>Visual Design</li>
                <li>Wireframing</li>
                <li>Prototyping</li>
              </ul>
            </div>
            <div class="category">
              <h4>Development</h4>
              <ul>
                <li>Vue.js</li>
                <li>React</li>
                <li>HTML5/CSS3</li>
                <li>JavaScript/TypeScript</li>
              </ul>
            </div>
            <div class="category">
              <h4>Tools</h4>
              <ul>
                <li>Figma</li>
                <li>Adobe Creative Suite</li>
                <li>Git</li>
                <li>VS Code</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// Component logic here
</script>

<style scoped>
.about {
  min-height: 100vh;
  padding: 4rem 2rem;
  background-color: #f8f9fa;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

h1 {
  font-size: 2.5rem;
  color: #2c3e50;
  margin-bottom: 2rem;
  text-align: center;
}

.content {
  display: grid;
  gap: 3rem;
}

.bio {
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
}

.bio h2 {
  font-size: 2rem;
  color: #34495e;
  margin-bottom: 0.5rem;
}

.title {
  font-size: 1.2rem;
  color: #7f8c8d;
  margin-bottom: 1.5rem;
}

.description {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #2c3e50;
}

.skills {
  margin-top: 2rem;
}

.skills h3 {
  font-size: 1.8rem;
  color: #34495e;
  margin-bottom: 1.5rem;
  text-align: center;
}

.skill-categories {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.category {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.category h4 {
  font-size: 1.3rem;
  color: #3498db;
  margin-bottom: 1rem;
}

.category ul {
  list-style: none;
  padding: 0;
}

.category li {
  padding: 0.5rem 0;
  color: #2c3e50;
  border-bottom: 1px solid #eee;
}

.category li:last-child {
  border-bottom: none;
}
</style> 