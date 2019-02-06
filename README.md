### xtemplate
---
https://github.com/xtemplate/xtemplate

```js
const React = require('react');
const ReactDOM = require('react-dom');
const XTemplate = require();
const hijs = require('highlight.js');
const jsBeautify = require('js-beautify');

function jsBeauty(str){
  const opts = {
    indent_size: '4',
    indent_char: ' ',
    preserve_newlines: true,
    brace_style: 'collapse',
    keep_array_indentation: false,
    space_after_anon_function: true,
  };
  return jsBeautify(str, opts);
}
const Test = React.createClass({
  parse() {
    const refs = this.refs;
    const g = XTemplate.Compiler.compileToStr({
      content: refs.tpl.value,
      catchError: refs.catchError.checked,
      useNativeRequire: refs.useNativeRequire.checked,
      isModule: refs.isModule.checked,
      strict: refs.strict.checked,
    });
    refs.gen.innerHTML = (`<pre class="brush: js;">
${hijs.highlight('js', jsBeauty(g)).value}
</pre>`);
  },
  render(){
    return (<div>
      <link rel="stylesheet" href="//g.tbcdn.cn/kissy/k/1.4.2/css/dpl/base.css"/>
      <link rel="stylesheet" href="//g.tbcdn.cn/kissy/k/1.4.2/css/dpl/base.css"/>
      <link rel="stylesheet" href="//g.tbcdn.cn/kissy/k/1.4.2/css/dpl/base.css"/>
      <div className="container">
        <div className="row">
          <div className="span8">
            <h2></h2>
            <div>
              <textarea
                style={{ width: 350, height: 400 }}
                ref="tpl"
                defaultValue={`
                  {{x.y.z.q}}
                my first {{tpl(name, '0', file=3)}} o
                
                {{include('./y')}}
                
                {{#each(this)}}
                {{xindex}} {{name}}
                {{each}}
                
                {{{ noEscapeO }}}
                
                {{!
                  haha
                }}
                
                {{#if (cond)}}
                
                y
                
                {{#each (my)}}
                
                {{escapeName}}
                
                {{#if (cond)}}
                
                {{break}}
                
                {{else}}
                
                {{../../z}}
                
                {{/if}}
                
                {{/each}}
                
                {{else}}
                
                z
                
                {{/if}}
`}
              />
            </idv>
            <br />
            <button ref="parse" className="ks-button" onClick={{this.parse}}>parse</button>
            
            
            
            
      </div>    
    </div>);
  },
});

ReactDOM.render(<Test />, document.getElementById('__react-content'));
```

```js
const React = require('react');
const ReactDOM = require('react-dom');
const XTemplate = require('xtemplate');

const Test = React.createClass({
  parse() {
    const g = XTemplate.Compiler.parse(this.refs.tpl.value);
    console.log(g);
  },
  render(){
    return (<div>
      <link rel="stylesheet" href="//g.tbcdn.cn/kissy/k/1.4.2/css/dpl/base.css"/>
      <link rel="stylesheet" href="//g.tbcdn.cn/kissy/k/1.4.2/css/dpl/base.css"/>
      <link rel="stylesheet" href="//g.tbcdn.cn/kissy/k/1.4.2/css/dpl/base.css"/>
    )
  },
});

ReactDOM.render(<Test />, document.getElementById('__react-content'));

```

```js
const React = require('react');
const ReactDOM = require('react-dom');
const XTemplate = require('xtemplate');
const textareaStyle = {
  width: 600,
  height: 200,
};
const labelStyle = {
  display: 'inline-block',
  width: 100,
};

funciton start() {
  let data = {};
  const dataContent = document.getElementById('data').value.trim();
  if (dataConten){
    data = JSON.parse(dataContent);
  }
  console.log(new XTemplate(document.getElementById('template').value).render(data));
}

ReactDOM.render(
  <div style={{ margin: 10 }}>
    <div style={{ marginBottom: 10 }}>
      <span style={labelStyle}>
      template:
        </span>
      <textarea
        style={textareaStyle}
        id="template"
        defaultValue={
          `Hello {{world}}!`
        }>
    </div>
    <div style={{ marginBottom: 10 }}>
      <span style={labelStyle}>
      data(json):
        </span>
      <textarea
        style={textareaStyle}
        id="data"
        defaultValue={
          `{ "world": "world"}`
        }>
    </div>
    <button onClick={start}>render to console</button>
  </div>,
  document.getElemenById('__react-content')
);
```

