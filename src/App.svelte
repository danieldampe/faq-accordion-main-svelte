<script>
  import bgMobile from './images/background-pattern-mobile.svg'
  import bgDesktop from './images/background-pattern-desktop.svg'
  import iconStar from './images/icon-star.svg'
  import AccordionItem from './lib/AccordionItem.svelte'

  let items = [
    {
      title: 'What is Frontend Mentor, and how will it help me?',
      text: 'Frontend Mentor offers realistic coding challenges to help developers improve their frontend coding skills with projects in HTML, CSS, and JavaScript. It\'s suitable for all levels and ideal for portfolio building.'
    },
    {
      title: 'Is Frontend Mentor free?',
      text: 'Yes, Frontend Mentor offers both free and premium coding challenges, with the free option providing access to a range of projects suitable for all skill levels.'
    },
    {
      title: 'Can I use Frontend Mentor projects in my portfolio?',
      text: 'Yes, you can use projects completed on Frontend Mentor in your portfolio. It\'s an excellent way to showcase your skills to potential employers!'
    },
    {
      title: 'How can I get help if I\'m stuck on a challenge?',
      text: 'The best place to get help is inside Frontend Mentor\'s Discord community. There\'s a help channel where you can ask questions and seek support from other community members.'
    }
  ]

  items.forEach((item, index) => item.collapse = index !== 0)
</script>

<picture>
  <source 
    media="(min-width: 375px)" 
    srcset={bgDesktop} 
  >
  <img src={bgMobile} alt="" class="app-bg">
</picture>
<div class="faq-accordion">
  <div class="faq-accordion-hdr">
    <img class="faq-accordion-icon" src={iconStar} alt="Icon Star">
    <h1 class="faq-accordion-title">
      FAQs
    </h1>
  </div>
  <div class="faq-accordion-body">
    {#each items as item, index}
      <AccordionItem 
        {...item}
        handlerClick={() => {
          items = items.map((elm, i) => {
            elm.collapse = i !== index 
            return elm
          })
        }}
      />
    {/each}
  </div>
</div>

<style>
  .faq-accordion {
    position: relative;
    z-index: 999;
    width: clamp(328px, 85%, 534px);
    padding: 1.6rem;
    padding-bottom: 0;
    border-radius: .5rem;
    background-color: var(--c-white);
  }

  .faq-accordion-hdr {
    display: flex;
    align-items: center;
    column-gap: 1.45rem;
    margin-bottom: .3rem;
  }

  .faq-accordion-icon { 
    width: clamp(24px, 10%, 37px); 
    aspect-ratio: 1 / 1;
  }

  .faq-accordion-title { font-size: clamp(1.98rem, 4vw, 3.1rem); }

  @media screen and (min-width: 768px) {
    .faq-accordion { 
      padding: 2.25rem; 
      padding-bottom: 1rem;
    }
    .faq-accordion-hdr { column-gap: 1.25rem; }
  }
</style>
