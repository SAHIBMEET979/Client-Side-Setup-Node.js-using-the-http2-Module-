mkdir http2-streaming-client
cd http2-streaming-client
npm init
npm install http2

Create the Client Application:
const http2 = require('http2');

const client = http2.connect('http://localhost:3000');

const req = client.request({ ':path': '/' });

req.on('data', (chunk) => {
  // Handle the received data (streamed content) here
  console.log(chunk.toString());
});

req.on('end', () => {
  // Streaming is complete
  client.close();
});

req.end();

Run the Client:
node your-client-app.js
