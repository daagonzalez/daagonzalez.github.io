<script>
  import Navbar from "./Navbar.svelte";
  import Projects from "./Projects.svelte";
  import Contact from "./Contact.svelte";
  import Footer from "./Footer.svelte";

  import { scrollRef } from "svelte-scrolling";
</script>

<main>
  <Navbar />
  <section use:scrollRef={"home"} class="section">
    <div>
      <h2>About Me</h2>
    </div>
    <div>
      <p>
        Hello! I'm Daniel Gonzalez, a passionate Software Engineer with a knack
        for developing innovative solutions to complex problems. With a strong
        foundation in software development and a love for learning new
        technologies, I strive to create impactful software that makes a
        difference.
      </p>
    </div>
  </section>
  <section use:scrollRef={"projects"} class="section">
    <Projects />
  </section>
  <section use:scrollRef={"contact"} class="section">
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
    /* flex-direction: column; */
  }
</style>
