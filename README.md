https://dev.to/shafia/some-common-vercel-errors-548i

## Server Deployment steps
1. comment await commands outside api methods for solving gateway timeout error
```
//comment following commands
await client.connect();
await client.db("admin").command({ ping: 1 });
```
2. create vercel.json file for configuring server
```
{
  "version": 2,
  "builds": [
    {
      "src": "index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "index.js",
      "methods": ["GET", "POST", "PUT", "PATCH", "DELETE", "OPTIONS"]
    }
  ]
}
```
3. Add Your production domains to your cors configuration
//Must remove "/" from your production URL
app.use(
  cors({
    origin: [
      "http://localhost:5173",
      "https://cardoctor-bd.web.app",
      "https://cardoctor-bd.firebaseapp.com",
    ],
    credentials: true,
  })
);
