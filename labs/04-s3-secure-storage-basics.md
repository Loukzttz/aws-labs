# S3 Lab 4 — Secure Storage Basics

## Objective
Create and manage an S3 bucket while reinforcing secure-by-default storage, encryption, and region awareness.

## Steps Performed
1. Created an S3 bucket with a globally unique name in a selected region.
2. Left Block Public Access fully enabled.
3. Enabled default encryption (SSE-S3).
4. Uploaded an object to the bucket.
5. Verified the object was private by accessing the object URL and receiving an AccessDenied response.
6. Observed Bucket Owner Enforced object ownership (ACLs disabled).
7. Deleted the object and bucket to prevent charges.

## Results
- Successfully created and used an encrypted S3 bucket.
- Confirmed objects are private by default.
- Reinforced region-scoped behavior.
- Cleaned up all resources.

## Key Takeaways
- S3 uses buckets and objects, not a traditional file system.
- Buckets are region-based and require globally unique names.
- Modern S3 security uses IAM and bucket policies instead of ACLs.
- Block Public Access prevents accidental data exposure.