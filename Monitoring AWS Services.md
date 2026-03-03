### When did Alex disable the "S3 Public Access Block" feature?
#### Answer Example: 2025-12-31 15:30:45

***Run query:*** ```index=task2 eventName=PutBucketPublicAccessBlock```

***Answer:*** ```2025-12-31 17:48:12```

### What is the SID of the applied policy that made the bucket public?

***Run query:*** ```index=task2 eventName=PutBucketPolicy
| stats values(requestParameters.bucketPolicy.Statement{}.Sid) as sids by userIdentity.userName```

***Answer:*** ```xxxx```


### Which IP address started the bucket scan soon after it was exposed?

***Run query:*** xxxxxxxxxxxxxxx

***Answer:*** ```xxxx```


### How many filenames were attempted, and which file was exfiltrated?
#### Answer Example: 42, secrets.json

***Run query:*** xxxxxxxxxxxxxxx

***Answer:*** ```xxxx```