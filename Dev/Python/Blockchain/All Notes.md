Here is how every single block inside of the blockchain looks like:
``
```
==`block = {`== 
==`'index': 1,`== 
==`'timestamp': 1506057125.900785,`==
==`'transactions': [`==
	==`{`==
	==`'sender': "8527147fe1f5426f9dd545de4b27ee00",`== 
	==`'recipient': "a77f5cdfa2934df3954a5c7c7da5df1f",`== 
	==`'amount': 5,`== 
	==`}`== 
==`],`== 
==`'proof': 324984774000,`==
==`'previous_hash':  "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"`== 
==`}`==
```

his is what the request for a transaction will look like. It’s what the user sends to the server:

```
{
 "sender": "my address",
 "recipient": "someone else's address",
 "amount": 5
}
```

