# Doomcode
Domm

(function(){
  var urls=[
    'https://diekmann.github.io/wasm-fizzbuzz/doom/',
    'https://joeheyming.github.io/doom/',
    'https://silentspacemarine.com/'
  ];
  var current=0;

  var ov=document.createElement('div');
  ov.style.cssText='position:fixed;inset:0;background:#000;z-index:2147483647;display:flex;flex-direction:column;';

  /* barra topo */
  var bar=document.createElement('div');
  bar.style.cssText='display:flex;align-items:center;justify-content:space-between;padding:6px 12px;background:#111;flex-shrink:0;';

  var title=document.createElement('span');
  title.textContent='💀 DOOM';
  title.style.cssText='color:#c00;font-family:monospace;font-size:18px;font-weight:bold;';

  var btns=document.createElement('div');
  btns.style.cssText='display:flex;gap:8px;align-items:center;';

  var src=document.createElement('span');
  src.id='doom-src';
  src.textContent='Fonte 1';
  src.style.cssText='color:#555;font-family:monospace;font-size:11px;';

  var next=document.createElement('button');
  next.textContent='Próxima fonte';
  next.style.cssText='background:#333;color:#aaa;border:none;padding:4px 10px;font-size:12px;border-radius:4px;cursor:pointer;';
  next.onclick=function(){
    current=(current+1)%urls.length;
    document.getElementById('doom-src').textContent='Fonte '+(current+1);
    document.getElementById('doom-frame').src=urls[current];
  };

  var cls=document.createElement('button');
  cls.textContent='✕ Fechar';
  cls.style.cssText='background:#c00;color:#fff;border:none;padding:4px 12px;font-size:12px;font-weight:bold;border-radius:4px;cursor:pointer;';
  cls.onclick=function(){document.body.removeChild(ov);};

  btns.appendChild(src);
  btns.appendChild(next);
  btns.appendChild(cls);
  bar.appendChild(title);
  bar.appendChild(btns);

  /* iframe */
  var frame=document.createElement('iframe');
  frame.id='doom-frame';
  frame.src=urls[0];
  frame.style.cssText='flex:1;width:100%;border:none;background:#000;';
  frame.allow='fullscreen;autoplay';

  ov.appendChild(bar);
  ov.appendChild(frame);
  document.body.appendChild(ov);
  frame.focus();
})();
