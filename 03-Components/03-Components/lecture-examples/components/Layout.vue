<template>
  <article>
    <slot name="header">
      <header>
        <h1>Default slot header</h1>
      </header>
    </slot>
    <section>
      <slot />
    </section>

    <slot name="footer">
      <footer>
        <h1>Default slot footer</h1>
      </footer>
    </slot>
  </article>
</template>
