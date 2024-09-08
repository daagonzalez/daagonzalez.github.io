<script>
  import Navbar from "./Navbar.svelte";
  import Home from "./Home.svelte";
  import Projects from "./Projects.svelte";
  import Contact from "./Contact.svelte";
  import Footer from "./Footer.svelte";

  import { scrollRef } from "svelte-scrolling";

  const sections = [
    { component: Home, ref: "home" },
    { component: Projects, ref: "projects" },
    { component: Contact, ref: "contact" },
  ];
</script>

<main>
  <Navbar />
  {#each sections as { component: SectionComponent, ref }}
    <section
      class="h-screen flex justify-center items-center text-center flex-col md:flex-row"
      use:scrollRef={ref}
    >
      <SectionComponent />
    </section>
  {/each}
  <Footer />
</main>
