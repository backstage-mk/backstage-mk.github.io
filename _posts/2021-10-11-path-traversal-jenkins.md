---
title: "Path Traversal | Jenkins"
author: Mümin Köykıran
date: "2021-10-11"
categories: 
  - "Vulnerability Research"
tags: 
  - "vulnerability research"
  - "jenkins"
image:
  src: /asset/path-traversal-jenkins/jenkins.jpg
---

**Software**: [Jenkins](https://www.jenkins.io/)

**Version**: 2.314

**Bug**: Path Traversal

**CVE**: CVE-2021-21683

**Description of the product:**

> The file browser in Jenkins 2.314 and earlier, LTS 2.303.1 and earlier may interpret some paths to files as absolute on Windows, resulting in a path traversal vulnerability allowing attackers with Overall/Read permission (Windows controller) or Job/Workspace permission (Windows agents) to obtain the contents of arbitrary files.


**Summary:**

The vulnerability allows a remote attacker to perform directory traversal attacks. Also The vulnerability exists due to input validation error when processing directory traversal sequences on Windows.

**Fix:**

> Upgrade to version org.jenkins-ci.main:jenkins-core:2.315,2.303.2 [Learn More](https://www.jenkins.io/security/advisory/2021-10-06/#SECURITY-2481)