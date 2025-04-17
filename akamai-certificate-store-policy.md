# Akamai Certificate Store Policy

This document is Copyright 2025, Akamai Technologies, Inc, and is
freely-usable under the terms of the
[Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0).

Questions and feedback about this policy can be emailed to
[trust-store@akamai.com](mailto:trust-store@akamai.com) or
[report an issue](https://github.com/akamai/akamai-certificate-store/issues).

Akamai maintains a *certificate store*, the default list of Certification
Authorities (CAs) that the Akamai CDN trusts when connecting our customer
origin sites. This store is global and used for all customers by default[^1].

Many other entities -- notably browsers -- have the same thing, but often
call it a "root store" or "trust store." These organizations generally run a
program to maintain the list of certificates in their store. An important
quality of most of these programs is that they are transparent, and perform
their work in public. The Mozilla Root Store was one of the first such
programs and all the work is done on their
[mailing list](https://groups.google.com/a/mozilla.org/g/dev-security-policy).

Most root programs require any listed CA to meet the requirements of the
CA/Browser forum. For Akamai's purposes, our requirements are found in
[Baseline Requirements for TLS Server Certificates](https://cabforum.org/working-groups/server/baseline-requirements/documents/).
Unlike some of the other trust stores, we do not care about things like
S/MIME certificates.

Akamai's policy for the certificate store is very simple. In order to be added, a CA must be in the trust store of all of the following organizations:

- [Apple Root Certificate List](https://support.apple.com/en-us/121672) [(policy)](https://www.apple.com/certificateauthority/ca_program.html)  
- [Chrome Root Store](https://g.co/chrome/root-store) [(policy)](https://g.co/chrome/root-policy)  
- [Microsoft Trusted Root Store](https://learn.microsoft.com/en-us/security/trusted-root/participants-list) [(policy)](https://aka.ms/RootCert)  
- [Mozilla Root Store](https://wiki.mozilla.org/CA/Included_Certificates) [(policy)](https://www.mozilla.org/en-US/about/governance/policies/security-group/certs/policy/)

The contents of the Akamai certificate store are
[publicly available](https://github.com/akamai/akamai-certificate-store)
(updated monthly). If a customer needs a CA to be added, and it is listed
with all of the above programs, contact us as listed above. Showing proof of
inclusion, and explaining your business needs will help expedite the process.
We update our store several times a year. Of course, we reserve the right to
not add a CA or otherwise modify the store's contents as we see fit.

The organizations in our list sometimes remove a CA from their store. While
this is generally a fairly public action, known across the industry, we also
compare our store against those listed above and mark for removal any CA that
is no longer trusted by all. At Akamai, our first obligation is to our
customers, so we need to be careful that if we remove a CA from the default
list, it will not impact any of them. Therefore, we need to be more careful
about removal than the browsers, who prioritize the overall safety of the
Internet first.

In a related manner, we have 21 CAs that were in the store before this policy
was implemented. We would like to remove these exceptions, but as noted
above, we will be doing this carefully over time so that we do not DoS our
customers.


[^1]:  For information about adding a private CA to validate your origin, see
the "Choose your Own" section of the Akamai
["Origin Server"](https://techdocs.akamai.com/property-mgr/docs/origin-server)
documentation or ask your Akamai support contact.
