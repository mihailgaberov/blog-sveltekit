<script>
import { space } from "svelte/internal";

</script>
<footer>
    <span>twitter | github</span>
    <span>© Mihail Gaberov 2022. All rights reserved.</span>
</footer>

  <style>
    footer {
        padding: 1rem;
        background: lightskyblue;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
      }
    
      span:first-child {
        margin: 0;
        list-style-type: none;
        display: flex;
        gap: 1rem;
      }
  </style>