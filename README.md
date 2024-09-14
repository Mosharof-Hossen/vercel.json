https://dev.to/shafia/some-common-vercel-errors-548i

##Server Deployment steps
1. comment await commands outside api methods for solving gateway timeout error
```
//comment following commands
await client.connect();
await client.db("admin").command({ ping: 1 });
```
