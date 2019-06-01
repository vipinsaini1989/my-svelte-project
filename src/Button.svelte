<style>
  button {
    margin-top: 1rem;
    font: inherit;
    padding: 0.25rem 0.5rem;
    border: 1px solid #007bff;
    background-color: #007bff;
    color: white;
    cursor: pointer;
  }

  button:hover,
  button:active {
    box-shadow: 1px 1px 6px rgba(0, 0, 0, 0.26);
  }
</style>

<button on:click>
  <slot />
</button>
