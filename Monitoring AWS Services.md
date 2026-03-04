
[Link to TryHackMe Room](https://tryhackme.com/room/monitoringawsservices "Link to room")

---

### When did Alex disable the "S3 Public Access Block" feature?
#### Answer Example: 2025-12-31 15:30:45

***Run query:*** ```index=task2 eventName=PutBucketPublicAccessBlock```

***Answer:*** ```2025-12-31 17:48:12```

---

### What is the SID of the applied policy that made the bucket public?

***Run query:*** ```index=task2 eventName=PutBucketPolicy | stats values(requestParameters.bucketPolicy.Statement{}.Sid)```

***Answer:*** ```TempAccessDeniedDebug```

---

### Which IP address started the bucket scan soon after it was exposed?

***Run query:*** ```index=task2 eventName=ListObjects | where eventTime > strptime("2025-12-31 17:48:12", "%Y-%m-%d %H:%M:%S") | search "userIdentity.accountId"=anonymous```

***Answer:*** ```212.8.250.220```

---

### How many filenames were attempted, and which file was exfiltrated?
#### Answer Example: 42, secrets.json

***Run query:*** ```index=task2 eventName=GetObject "userIdentity.accountId"=anonymous eventCategory=Data errorCode=success```

***Answer:*** ```53, repo.zip```

---

### Which security group did Emma create, and which risky service did it expose?
#### Answer Example: bastion-public-access, RDP

***Run query:*** ```index=task3 eventName=CreateSecurityGroup```
***Run query:*** ```index=task3 eventName=AuthorizeSecurityGroupIngress```

***Answer:*** ```website-access-sg, SSH```

---

### Which EC2 instance ID was created shortly after and uses that security group?

***Run query:*** ```index=task3 eventName=RunInstances```

***Answer:*** ```i-082579354380296e6```

---

### According to the GuardDuty alert, which IP soon attacked the instance?

***Run query:*** ```index=task3 app="AWS GuardDuty"```

***Answer:*** ```45.78.205.134```

---

### When did Emma revoke the insecure rule from the security group?
#### Answer Example: 2025-12-31 20:30:45

***Run query:*** ```index=task3 eventName=RevokeSecurityGroupIngress```

***Answer:*** ```2025-12-31 21:58:34```

---

### What is the name (instance identifier) of the created RDS instance?

***Run query:*** ```index=task4 eventName=CreateDBInstance```

***Answer:*** ```db-thm-preprod-qa```

---

### Which two events indicate the database is Internet-exposed?
#### Provide the first part of their eventID in chronological order.
#### Answer Example: 0a1b2c3d, 1b2c3d4f

***Run query:*** ```index=task4 eventName=Modify*```

***Answer:*** ```dcb54877, 0a3b23c1```

---

### What was the second Discovery command the adversary ran?

***Run query:*** ```index=task5 eventName=List*```

***Answer:*** ```ListAttachedUserPolicies```

---

### Which other IAM user did the adversary discover and backdoor?

***Run query:*** ```index=task5 user!="jose.martinez"```

***Answer:*** ```lars.andersen```

---

### What does the acronym DoW stand for?

***Answer:*** ```Denial of Wallet```

---

### Should you monitor DoW with the same effort as DoS? (Yea/Nay)

***Answer:*** ```Yea```

