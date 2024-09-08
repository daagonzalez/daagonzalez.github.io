<script>
  import Footer from "./Footer.svelte";

  import Navbar from "./Navbar.svelte";
  import Projects from "./Projects.svelte";
  import Contact from "./Contact.svelte";
</script>

<main>
  <Navbar />
  <section id="home" class="section">
    <h2>About Me</h2>
    <p>
      Hello! I'm Daniel Gonzalez, a passionate Software Engineer with a knack
      for developing innovative solutions to complex problems. With a strong
      foundation in software development and a love for learning new
      technologies, I strive to create impactful software that makes a
      difference.
    </p>
  </section>
  <section id="projects" class="section">
    <Projects />
  </section>
  <section id="contact" class="section">
    <Contact />
  </section>
  <Footer />
</main>

<style>
  .section {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    flex-direction: column;
  }
</style>
