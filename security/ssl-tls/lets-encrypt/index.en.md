+++
title = "Let's Encrypt Certificates"
layout = "man"
weight = 2
tags = ["https", "security", "ssl"]
+++

[Let's Encrypt](https://letsencrypt.org) is a certification authority that proposes a simple way to generate free certificates. The certificates offered are [Domain Validation](https://en.wikipedia.org/wiki/Domain-validated_certificate) type ones, valid for [90 days](https://letsencrypt.org/2015/11/09/why-90-days.html).

## Automatically generated certificates

alwaysdata automatically generates and renews a Let's Encrypt certificate for every address pointing to our servers and it is added in the **Web > Sites** section. Hence, every site hosted on its servers handles HTTPS protocol.

You can view them in the **Advanced > SSL certificates > Automatically generated certificates** section:

{{< fig "images/admin-panel_autogenerated-certificates.en.png" "Administration interface: automatically generated certificates" >}}

*.alwaysdata.net* addresses are handled by the `*.alwaysdata.net` wildcard certificate returned by default by the servers.

{{% notice note %}}
From 20 SSL certificates per domain, i.e. from the 20th subdomain has been added to **Web > Sites**, the system will generate a wildcard certificate to manage the following subdomains.
{{% /notice %}}

{{% notice warning %}}
Certificate generation is limited to 64 characters per complete address.
{{% /notice %}}

### The SSL certificate is automatically generated and renewed, you will find it in the "Auto-generated certificates" menu.

To avoid duplicates, alwaysdata blocks Let's Encrypt certificate generation for all addresses that are already generated automatically. You can contact [support](https://admin.alwaysdata.com/support/add) if you wish to completely manage SSL certificate generation for a domain.

The creation of these certificates is **dependent on DNS propagation**: the address must point to alwaysdata servers. Once the address is added in **Web > Sites**, the system will attempt to generate its certificate *every 30 minutes for 24 hours*. This will then change to *once a day*.

{{% notice tip %}}
People who add the addresses before changing the DNS records can, after making the changes with their DNS provider, restart - once - autogeneration by deleting the addresses from the site in **Web > Sites** and putting them back a few seconds later.
{{% /notice %}}


## Wildcard certificates

When a domain use our [DNS servers]({{<ref "remote-access/login-details">}}), it is possible to generate a [wildcard certificate](https://en.wikipedia.org/wiki/Wildcard_certificate) - *.example.org structure - in **Advanced > SSL certificates > Add a SSL certificate > Create a Let's Encrypt certificate**. This certificate will be automatically renewed by the system.

---
## Links

- [List of browser compatibilities](https://letsencrypt.org/docs/certificate-compatibility/)
- [Certbot](https://certbot.eff.org/): ACME client to generate your own certificates
