var dpr, rem, scale;
    var docEl = document.documentElement;
    var fontEl = document.createElement('style');
    var metaEl = document.querySelector('meta[name="viewport"]');
    dpr = window.devicePixelRatio || 1;
    function makeFontSize () {
      if (docEl.clientWidth == 0) {
        setTimeout(makeFontSize, 5)
        return
      }
      var w = docEl.clientWidth > 560 ? 560 : docEl.clientWidth;
      rem = w * dpr / 10;
      scale = 1 / (dpr);
      docEl.setAttribute('data-dpr', dpr);
      docEl.firstElementChild.appendChild(fontEl);
      fontEl.innerHTML = 'html{font-size:' + rem / dpr + 'px!important;overflow-x: hidden;}';
    }
    makeFontSize()
