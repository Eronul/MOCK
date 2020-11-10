实现一个简易的server-mock
const http = require('http')
const fs = require('fs')
const url = require('url')

http.createServer((req, res) => {
    let urlObj = url.parse(req.url)
    console.log(urlObj)

    if(urlObj.pathname === '/getWeather') {
        res.end(JSON.stringify( {data: '晴'} ))
    }else {
        res.end(fs.readFileAsync(__dirname +'/index.html'))
    }
    res.end('hello world')
}).listen(8888)  

console.log('open http://localhsot:8888')
