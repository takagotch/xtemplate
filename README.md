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

```
```

```
```

