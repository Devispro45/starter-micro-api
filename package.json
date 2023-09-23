const http = require('http');
const https = require('https');
const fs = require('fs');

const port = 8080;
const proxyHost = 'example.com';
const proxyPort = 80;

const server = http.createServer((req, res) => {
  const options = {
    hostname: proxyHost,
    port: proxyPort,
    path: req.url,
    method: req.method,
    headers: req.headers,
  };

  const proxyReq = http.request(options, (proxyRes) => {
    res.writeHead(proxyRes.statusCode, proxyRes.headers);
    proxyRes.pipe(res);
  });

  req.pipe(proxyReq);
});

server.listen(port, () => {
  console.log(`Proxy server is running on port ${port}`);
});
