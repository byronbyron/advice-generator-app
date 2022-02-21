<script context="module">
  export async function load({ fetch }) {
    const res = await fetch('https://api.adviceslip.com/advice');
    const advice = await res.json();

    if (res.ok) {
      return {
        props: {
          advice
        }
      }
    }

    return {
      status: res.status,
      error: new Error('Could not fetch advice.')
    }
  }
</script>

<script>
  export let advice;
</script>

<div>
  <!-- <p>Advice #117</p> -->
  <!-- <h1>&ldquo;It is easy to sit up and take notice, what&lsquo;s difficult is getting up and taking action.&rdquo;</h1> -->

  <p>Advice #{advice.slip.id}</p>
  <h1>&ldquo;{advice.slip.advice}&rdquo;</h1>

  <picture>
    <source srcset="/pattern-divider-desktop.svg"
            media="(min-width: 992px)">
    <img src="/pattern-divider-mobile.svg" alt="divider" />
  </picture>

  <button onClick="window.location.reload()">
    <span class="sr-only">New advice quote...</span>
    <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M20 0H4a4.005 4.005 0 0 0-4 4v16a4.005 4.005 0 0 0 4 4h16a4.005 4.005 0 0 0 4-4V4a4.005 4.005 0 0 0-4-4ZM7.5 18a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Z" fill="#202733"/></svg>
  </button>
</div>
