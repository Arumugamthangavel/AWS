# AWS Identity and Access Management

Usually called:
IAM

---

What IAM Actually Is
---
IAM controls:

WHO can do WHAT on WHICH resource

Real World Analogy
---
Imagine AWS is a massive company building.

IAM decides:

| Person          | Allowed?         |
| --------------- | ---------------- |
| Security guard  | Only gate access |
| HR              | Employee files   |
| DevOps engineer | Servers          |
| CEO             | Everything       |


---

# IAM Main Components

![Image](https://images.openai.com/static-rsc-4/Cda2NxL6YhAdqZ0lqJSu2bdCHkWqC2v8O-QIoorouIbJ4uWWhvSmFWqI4-C8sa3CtTSQvfHBLYJNpI3W1rfpf0NjKDqfbXQ-aAZQiK_hDafg30rrrPnqFfdWuxtri_vZ0hNvydOUUpy1f7wYuhgjgKQAI7XUZ9smYXUI0-MIJtu0JvvyDc6n0ofhcooo_rwE?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/EF4YmsnqMKGVJ2m2BAMWTbmwcbCmfusOqpKecHlQutdPEWn1wAVzqdki7olnut9xmutD5-Qnm6DJKLn_4C6SPtZ55e4pE0pcydQR2-n0bOFZ_pkrapoYGKx_1V4uvlCADSPxn-wDm7lEayO6N73zJ8-B95nwgCfHoyKIuh8f8Yh3zrNudrAj7_MbPOaIs4TG?purpose=fullsize)

There are 4 pillars.

---

# 1) IAM Users

 Individual identities

Example:

```text id="r31cn10"
arumugam
devops-engineer
intern-user
```

Each user gets:

* username
* password
* access keys (optional)



# 2️) IAM Groups

Groups = collection of users.

Example:

```text id="ylz8x7"
DevOps-Team
Developers
Interns
```

Instead of assigning permissions one by one:

👉 Add user to group


---

# 3️) IAM Policies (MOST IMPORTANT)

Policies = permission documents.

Written in JSON.

They define:

```text id="q9ol9e"
Allow / Deny
```

Example:

```json
{
  "Effect": "Allow",
  "Action": "ec2:*",
  "Resource": "*"
}
```

Meaning: Can do anything in EC2


Think of Policies as RULEBOOKS
---
They answer:

```text id="vtx7e9"
What actions are allowed?
```

---

# 4️) IAM Roles (VERY IMPORTANT FOR DEVOPS)

Roles are temporary permissions.

Used by:

* EC2
* Lambda
* Services

---

# 🔥 Example (Classic Interview Question)

Question:

```text id="a8gq6m"
How does EC2 access S3 securely?
```

Correct answer:

```text id="g9skt7"
Using IAM Role
```




We do simple industry-style setup.

---

# TASK 1 — Create IAM User

Go to:

IAM → Users → Create User

Name:

```text id="z6zt17"
devops-user
```

Enable:

AWS Management Console access

Set password.

---

# TASK 2 — Create Group

Create group:

```text id="4ey8q8"
DevOps-Team
```

Attach policy:

```text id="n1y5u8"
AmazonEC2ReadOnlyAccess
```

---

# TASK 3 — Add User to Group

Add:

```text id="mcg7ud"
devops-user
```

to:

```text id="b3xv0r"
DevOps-Team
```

---

# TASK 4 — Login as IAM User

Sign out root account.

Login using IAM user URL.

Now test:

=> Can view EC2
=> Cannot delete EC2

That’s permission control.

---


