<script>
/* eslint-disable no-new-func */

import Highlight from 'highlight.js'

export default {
  props: {
    renderFn: {
      type: String,
      default: ''
    },
    staticRenderFn: {
      type: String,
      default: ''
    }
  },
  created() {
    this.templateRender = new Function(this.renderFn)()
    this.$options.staticRenderFns = new Function(this.staticRenderFn)()
  },
  mounted() {
    for (const element of document.querySelectorAll('pre code')) {
      Highlight.highlightBlock(element)
    }
  },
  render() {
    return this.templateRender ? this.templateRender() : <div>Rendering</div>
  }
}
</script>

<style lang="scss" scoped>
$content-width: 55rem;
$normal-font: 1rem;
$syntax-color: #b0cdf3;
$syntax-bg: #011627;

code, kbd, pre, samp {
  font-family: monospace;
}

code {
  font-size: 1rem;
  font-weight: 600;
  padding: 5px;
  border-radius: 5px;
}

pre {
  background: $syntax-bg;
  margin: 2em auto;
  code {
    color: $syntax-color;
    background: none;
    box-shadow: none;
    font-family: Consolas, Menlo, Monaco, source-code-pro, Courier New, monospace;
    font-size: 0.725rem;
    display: block;
    overflow-x: auto;
    max-width: $content-width;
    padding: 1.2em;
    margin: auto;
    line-height: 1.55em;
    text-align: left;
    white-space: pre;
    word-spacing: normal;
    word-break: normal;
    word-wrap: normal;
    tab-size: 2;
    hyphens: none;
    border-radius: 0;
  }
}

hr {
  width: auto;
  max-width: 47.5rem;
  float: none;
  display: block;
  border: 1px solid rgba(0, 0, 0, 0.12);
  padding: 0;
  margin: 50px auto;
  &:before {
    content: '';
    display: table;
  }
  &:after {
    content: '';
    display: table;
    clear: both;
  }
}

p, h1, h2, h3, h4, h5, h6, ul, ol, iframe, table {
  width: auto;
  max-width: $content-width;
  float: none;
  display: block;
  padding: 0 1.25rem;
  margin: 0 auto 2rem;
  font-weight: 300;
  font-style: normal;
  font-size: $normal-font;
  line-height: 2;
  letter-spacing: .01rem;
  &:before {
    content: '';
    display: table;
  }
  &:after {
    clear: both;
  }
}

em {
  margin-right: 2.5px;
}

blockquote {
  width: auto;
  max-width: 45.625rem;
  float: none;
  display: block;
  border-left: .313rem solid #5E72E4;
  padding: 0 1.875rem;
  margin: 2.25rem auto;
  p {
    color: rgba(0, 0, 0, 0.6);
    margin: 0;
  }
  &:before {
    content: '';
    display: table;
  }
  &:after {
    content: '';
    display: table;
    clear: both;
  }
}

h1, h2, h3, h4, h5, h6 {
  font-weight: 800;
  margin-bottom: 10px;
  line-height: 1.4;
}

p, li {
  font-size: $normal-font;
  color: #555;
  strong {
    font-weight: 600;
  }
  a {
    font-weight: 400;
    border-bottom: 0.1rem dashed #5E72E4;
  }
  code {
    margin: 0 0.15rem;
    background: $syntax-bg;
    color: $syntax-color;
  }
}

h1 {
  font-size: 2rem;
}

h2 {
  font-size: 1.8rem;
}

h3 {
  font-size: 1.5rem;
}

h4 {
  font-size: 1.3rem;
}

h5 {
  font-size: 1.2rem;
}

h6 {
  font-size: 1.1rem;
}

ul, ol {
  padding-left: 2.5rem;
}

img {
  max-width: 100%;
  margin: 1.875rem auto;
  display: block;
}

iframe {
  margin-top: 1.875rem;
  width: 100%;
}

@media only screen and (max-width: 50rem) {
  blockquote, hr {
    width: 70%;
  }
  blockquote p {
    font-size: 1.125rem;
    line-height: 1.5;
    padding: 0;
  }
}
</style>
