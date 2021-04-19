<!-- Used for looping over lists of data -->
<script>
  let cats = [
    { id: "J---aiyznGQ", name: "Keyboard Cat" },
    { id: "z_AbfPXTKms", name: "Maru" },
    { id: "OUtn3pvWmpg", name: "Henri The Existential Cat" },
  ];
</script>

<h2>The Famous Cats of Youtube</h2>

<ul>
  <!-- loop through the array, the second arg is the index -->
  <!-- {#each cats as cat, i}  Would need to use cat. for id and name -->

  <!-- destructured syntax -->
  {#each cats as { id, name }, i}
    <li>
      <a target="_blank" href="https://www.youtube.com/watch?v={id}">
        {i + 1}: {name}
      </a>
    </li>
  {/each}
</ul>
