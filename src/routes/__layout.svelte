<script>
  import 'normalize.css';
  import '../app.css';
  import Header from '../components/Header.svelte'
  import Footer from '../components/Footer.svelte'
</script>

<Header />

<main>
  <slot></slot>
</main>

<Footer />
