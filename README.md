# S3 Bucket Security Project

This project documents my hands-on practice securing an AWS S3 bucket using IAM policies and bucket policies.

---

## 🛠️ What I Did

✅ Created an S3 bucket: `chandan-saa-project-bucket`  
✅ Uploaded a test object (`ny.jpg`)  
✅ Applied a public-read bucket policy to intentionally misconfigure access  
✅ Verified public access by loading the object in an incognito window  
✅ Enabled Block Public Access + removed the bucket policy to secure the bucket  
✅ Verified access is denied when tested anonymously

---

## 📸 Screenshots Included

- Bucket creation configuration  
- File upload summary  
- Public-read bucket policy applied  
- Public access working (incognito test)  
- Block Public Access enabled  
- Access Denied (post-securing)  
- IAM policy JSONs (misconfigured + secure versions)

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
       



