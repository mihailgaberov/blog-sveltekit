<script>
    export let title = ''
    export let date = 'Somewhere in the time'
  </script>
  
  <h1>{title}</h1>
  
  <p>Published: {date}</p>
  
  <slot />