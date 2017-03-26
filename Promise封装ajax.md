```
function ajax(url) {
  return new Promise(function(resolve, reject){
    var xml = new XMLHttpRequest();
    xml.open('get',url,true);
    xml.onload = resolve;
    xml.onerror = reject;
    xml.send();
  } )
}
```

```
ajax(url).then(function(response)).catch(function(err))
```