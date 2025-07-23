# S3 Bucket Security Project

This project documents my hands-on practice securing an AWS S3 bucket using IAM policies, bucket policies, and access logging.

---

## 🛠️ What I Did

✅ Created an S3 bucket: `chandan-saa-project-bucket`  
✅ Uploaded a test object (`ny.jpg`)  
✅ Applied a public-read bucket policy to intentionally misconfigure access  
✅ Verified public access by loading the object in an incognito window  
✅ Enabled Block Public Access + removed the bucket policy to secure the bucket  
✅ Verified access is denied when tested anonymously  
✅ Enabled **Server Access Logging** for auditing

---

## 📸 Screenshots Included

- Bucket creation configuration  
- File upload summary  
- Public-read bucket policy applied  
- Public access working (incognito test)  
- Block Public Access enabled  
- Access Denied (post-securing)  
- IAM policy JSONs (misconfigured + secure versions)  
- Server access logging setup screen

---

## 🔐 Key IAM Policy (Public-Read, Misconfiguration Example)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::chandan-saa-project-bucket/*"
    }
  ]
}
```

---

## 📊 Server Access Logging (Auditing)

To enhance auditing and traceability, I enabled **S3 Server Access Logging**.

**Logging Configuration:**
- **Logging Target Bucket:** `s3-accesslogs-chandan`
- **Log Object Key Format:**  
  `[DestinationPrefix]/[SourceAccountId]/[SourceRegion]/[SourceBucket]/[YYYY]/[MM]/[DD]/[YYYY]-[MM]-[DD]-[hh]-[mm]-[ss]-[UniqueString]`
- **Source of Date Used:** `S3 Event Time`

**Sample Log Key Structure:**
```
799468650423/us-east-1/chandan-saa-project-bucket/2025/07/01/2025-07-01-00-00-00-[UniqueString]
```

---

## ✅ Outcome

Successfully simulated a misconfigured S3 bucket, applied access restrictions, and implemented logging to monitor access — demonstrating foundational S3 security practices and audit readiness.
