<script>
  import Header from './Header.svelte';
  import Footer from './Footer.svelte';
</script>

<main>
  <Header name="Daniel Gonzalez" jobTitle="Software Engineer" />
  
  <section id="about">
    <h2>About Me</h2>
    <p>Hello! I'm Daniel Gonzalez, a passionate Software Engineer with a knack for developing innovative solutions to complex problems. 
    With a strong foundation in software development and a love for learning new technologies, I strive to create impactful software 
    that makes a difference.</p>
  </section>
  
  <Footer />
</main>

<style>
  section {
    padding: 20px;
  }
</style>
