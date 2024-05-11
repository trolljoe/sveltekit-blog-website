<script lang="ts">
  import { cubicOut } from 'svelte/easing';
  import { crossfade } from 'svelte/transition';

  const glitch = (node: HTMLElement, { delay = 0, duration = 300 }) => {
    const squares = [];
    const interval = setInterval(() => {
      const square = document.createElement('div');
      square.classList.add('glitch-square');
      square.style.left = `${Math.random() * 100}%`;
      square.style.top = `${Math.random() * 100}%`;
      node.appendChild(square);
      squares.push(square);
      setTimeout(() => {
        squares.forEach(square => node.removeChild(square));
      }, duration);
    }, delay);

    return {
      delay,
      duration,
      tick: t => {
        if (t === 1) clearInterval(interval);
      },
      css: (t, u) => {
        return `
          opacity: ${t};
        `;
      }
    };
  };

  const glitchTransition = (node, opts) => {
    const duration = opts.duration || 300;
    const delay = opts.delay || 0;
    return {
      delay,
      duration,
      css: t => {
        const easeOut = cubicOut(t);
        return `opacity: ${easeOut};`;
      },
      tick: t => {
        if (t === 1) node.style.opacity = '1';
      }
    };
  };
</script>

{#key url}
  <div class="glitch" transition:glitch={{ delay: 0, duration: 100 }} in:glitchTransition={{ delay: 0, duration: 100 }}>
    <slot />
  </div>
{/key}

<style>
  .glitch {
    height: 100%;
  }

  .glitch-square {
    position: absolute;
    width: 10px;
    height: 10px;
    background-color: green;
    opacity: 0.7;
  }
</style>
