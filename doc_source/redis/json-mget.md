# JSON\.MGET<a name="json-mget"></a>

Gets serialized JSONs at the path from multiple document keys\. It returns null for a nonexistent key or JSON path\.

Syntax

```
JSON.MGET <key> [key ...] <path>
```
+ key \(required\) – One or more Redis keys of document type\.
+ path \(required\) – A JSON path\.

**Return**
+ Array of bulk strings\. The size of the array is equal to the number of keys in the command\. Each element of the array is populated with either \(a\) the serialized JSON as located by the path or \(b\) null if the key does not exist, the path does not exist in the document, or the path is invalid \(syntax error\)\.
+ If any of the specified keys exists and is not a JSON key, the command returns `WRONGTYPE` error\.

**Examples**

 Enhanced path syntax:

```
127.0.0.1:6379> JSON.SET k1 . '{"address":{"street":"21 2nd Street","city":"New York","state":"NY","zipcode":"10021"}}'
OK
127.0.0.1:6379> JSON.SET k2 . '{"address":{"street":"5 main Street","city":"Boston","state":"MA","zipcode":"02101"}}'
OK
127.0.0.1:6379> JSON.SET k3 . '{"address":{"street":"100 Park Ave","city":"Seattle","state":"WA","zipcode":"98102"}}'
OK
127.0.0.1:6379> JSON.MGET k1 k2 k3 $.address.city
1) "[\"New York\"]"
2) "[\"Boston\"]"
3) "[\"Seattle\"]"
```

 Restricted path syntax:

```
127.0.0.1:6379> JSON.SET k1 . '{"address":{"street":"21 2nd Street","city":"New York","state":"NY","zipcode":"10021"}}'
OK
127.0.0.1:6379> JSON.SET k2 . '{"address":{"street":"5 main Street","city":"Boston","state":"MA","zipcode":"02101"}}'
OK
127.0.0.1:6379> JSON.SET k3 . '{"address":{"street":"100 Park Ave","city":"Seattle","state":"WA","zipcode":"98102"}}'
OK

127.0.0.1:6379> JSON.MGET k1 k2 k3 .address.city
1) "\"New York\""
2) "\"Seattle\""
3) "\"Seattle\""
```