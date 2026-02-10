# JSON Web Signature (JWS)

JWS represents content secured with digital signatures or message authentication codes (MACs) using JSON-based data structures.


### Two Types of JWS Serialization

#### JWS Compact Serialization

JWS Compact Serialization represents digitally signed or MACed content as a compact, URL-safe string. 

- Example of flattened JWS JSON Serialization Syntax
```js
{
	"payload" : ,
	"protected" : ,
	"header" : {"kid" : ""},
	"signature" : "" 
}
```


# Compact Serialize and Deserialize

```python
from jose imort JsonWebSignature

jws = JsonWebSignature()

protected = {'alg' : 'HS256'}
payload = b'example'
secret = b'secret'
jws.serialize_compact(protected, payload, secret)

```

`jws.deserialize_compact()`:

1. Reads the JWS token (header + payload + signature)
2. Calls your `load_key(header, payload)` function to **get the key**
3. Verifies the signature with the correct key 
4. Returns the **claims** (the data inside the token) if valid

```python
jws = JsonWebSignature(algorithms=['RS256'])
protected = {'alg' : 'RS256'}
payload = b'example'

with open('private.pem', 'rb') as f:
	secret = f.read()
jws.serialize_compact(protected, payload, secret)
```

-- Deserialize:

```python
with open('public.pem', 'rb') as f:
	key = f.read()
	
data = jws.deserialize_compact(s, key)
jws_header = data['header']
payload = data['payload']
```
