<script>
  import iconMinus from '../images/icon-minus.svg'
  import iconPlus from '../images/icon-plus.svg'
  export let collapse = true
  export let title
  export let text
  export let handlerClick
</script>

<div class="faq-accordion-item">
  <button class="faq-accordion-item-hdr" on:click={handlerClick}>
    <h2 class="faq-accordion-item-title">{title}</h2>
    <img class="faq-accordion-item-icon" src={collapse ? iconPlus : iconMinus} alt="Icon">
  </button>
  <div class={`faq-accordion-item-body ${collapse ? 'collapse' : ''}`}>
    <div class="faq-accordion-item-body-inner">
      <div class="faq-accordion-item-body-content">
        <p class="faq-accordion-item-text">{text}</p>
      </div>
    </div>
  </div>
</div>

<style>
  .faq-accordion-item {
    display: flex;
    flex-direction: column;
    border-bottom: .1rem solid #f7f6fb;
  }
  .faq-accordion-item:last-child { border-bottom: none; }

  .faq-accordion-item-hdr {
    display: flex;
    justify-content: space-between;
    align-items: center;
    column-gap: 1.8rem;
    padding: 0;
    padding-block: 1.35rem;
    border-radius: initial;
    text-align: left;
    background-color: transparent;
  }
  .faq-accordion-item-hdr:hover { color: #a239d0; }

  .faq-accordion-item-title {
    font-size: 1rem;
    font-weight: 600;
  }

  .faq-accordion-item-icon { width: 1.6rem; }

  .faq-accordion-item-body {
    display: grid;
    grid-template-rows: 1fr;
    transition: grid-template-rows .25s ease-in-out;
  }
  .faq-accordion-item-body.collapse { grid-template-rows: 0fr; }
  .faq-accordion-item-body-inner { overflow: hidden; }
  .faq-accordion-item-body-content { padding-block: .25rem 1.2rem; }

  .faq-accordion-item-text {
    font-size: .865rem;
    font-weight: 400;
    color: var(--c-grayish-purple);
  }

  @media screen and (min-width: 768px) {
    .faq-accordion-item-hdr { column-gap: .5rem; }
  }
</style>
