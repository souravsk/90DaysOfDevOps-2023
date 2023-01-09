# Open Source Security

Open-source software has become widely used over the past few years due to its collaborative and community/public nature.

The term Open Source refers to software in the public domain that people can freely use, modify, and share.

The main reason for this surge of adoption and interest in Open Source is the speed of augmenting proprietary code developed in-house and this in turn can accelerate time to market. Meaning that leveraging OSS can speed up application development and help get your commercial product to market faster.

# What is Open-Source Security?

Open-source security refers to the practice of ensuring the safety and security of computer systems and networks that use open-source software. As we said above Open-source software is software that is freely available to use, modify, and distribute, and it is typically developed by a community of volunteers however there is a huge uptake from big software vendors that also contribute back to open-source, you only need to look at the Kubernetes repository to see which vendors are heavily invested there.

Because open-source software is freely available, it can be widely used and studied, which can help to improve its security. However, it is important to ensure that open-source software is used responsibly and that any vulnerabilities are addressed in a timely manner to maintain its security.

## 3 As of OSS Security

- **Assess** - Look at the project health, how active is the repository, and how responsive are the maintainers. If these show a bad sign, then you are not going to be happy about the security of the project.

At this stage, we can also check the security model, code reviews, data validations, and test coverage for security. How does the project handle CVEs?

What dependencies does this project have? Explore the health of these in turn as you need to be sure the whole stack is good.

- **Adopt** - If you are going to take this on within your software or as a standalone app within your own stack, who is going to manage and maintain it? Set some policies on who internally will overlook the project and support the community.
- **Act** - Security is the responsibility of everyone, not just the maintainers, as a user you should also act and assist with the project.

## Log4j Vulnerability

In early 2022 we had a vulnerability that seemed to massively hit the headlines (Log4j (CVE-2021-44228) RCE Vulnerability)

Log4j is a very common library for logging within Java. The vulnerability would in turn affect millions of java-based applications.

A malicious actor could use this vulnerability within the application to gain access to a system.

Two big things I mentioned,

- **millions** of applications will have this package being used.
- **malicious actors** could leverage this to gain access or plant malware into an environment.

The reason I am raising this is that security never stops, the growth of Open-Source adoption has increased this attack vector on applications, and this is why there needs to be an overall effort on security from day 0.