+++
url = "/fr/domaines/"
title = "Domaines"
pre = "<i class='fas fa-fw fa-server'></i> "
weight = 16
chapter = true
tags = ["dns", "domaine"]
+++

# Domaines

Les domaines sont gérés dans l'onglet **Domaines** de votre interface d'administration. [Achetez](https://www.alwaysdata.com/fr/domaines/#main), transférez ou ajoutez en gestion votre domaine. Revendeur [GANDI](https://www.gandi.net/fr), nous nous appuyons sur leur expérience pour vous proposer le plus d'extensions possibles. [Contactez-nous](https://admin.alwaysdata.com/support/add/) si l'extension souhaitée n'est pas proposée par défaut.

## Ressources

- [API - Domaine](https://api.alwaysdata.com/v1/domain/doc/)
- [Acheter un domaine]({{< relref "buy-a-domain" >}})
- [Transférer un domaine]({{< relref "transfer-a-domain" >}})
- [Ajouter un domaine externe]({{< relref "add-an-external-domain" >}})
- [Renouveler un domaine]({{< relref "renew-a-domain" >}})
- [Dates limites]({{< relref "deadlines" >}})
- [Déplacer un domaine]({{< relref "move-a-domain" >}})
- [Changer de propriétaire]({{< relref "change-of-owner" >}})
- [Mettre à jour les informations du propriétaire du domaine]({{< relref "update-owner-details" >}})
- [Déléguer un sous-domaine]({{< relref "delegate-a-subdomain" >}})
- [Détruire un domaine]({{< relref "wipe-a-domain" >}})
- [Transfert sortant]({{< relref "outgoing-transfer" >}})
- [Problèmes fréquents]({{< relref "./troubleshooting" >}})

## Gestion DNS

Vous pouvez aussi gérer vos DNS, via un système classique, directement dans l'onglet **Domaines**.

Pour utiliser nos serveurs DNS, indiquez chez votre registrar `dns1.alwaysdata.com` et `dns2.alwaysdata.com`.


- [API - Enregistrement DNS](https://api.alwaysdata.com/v1/record/doc/)
- [Ajouter un enregistrement DNS]({{< relref "add-dns" >}})
- [Utiliser des MX externes]({{< relref "use-external-mx" >}})
- [Changer de serveurs DNS]({{< relref "change-of-dns-servers" >}})
- [Ajouter un enregistrement SRV]({{< relref "add-srv-record" >}})
- [Ajouter un enregistrement CAA]({{< relref "add-caa-record" >}})
- [Supprimer un enregistrement DNS]({{< relref "delete-dns" >}})

[DNSSEC](https://fr.wikipedia.org/wiki/Domain_Name_System_Security_Extensions) n'est pas encore géré.

{{% notice warning %}}
Officiellement invalides (d'après [IDNA2008](http://unicode.org/faq/idn.html)), nous ne supportons pas les **emojis** dans un nom de domaine. Notre infrastructure utilise la [bibliothèque Python `idna`](https://github.com/kjd/idna), qui [respecte impérativement](https://github.com/kjd/idna/issues/18) IDNA2008 à ce stade.
{{% /notice %}}

{{% notice info %}}
Étant revendeurs GANDI vous pouvez recevoir des mails de notre part, de la leur et des [registres](https://fr.wikipedia.org/wiki/Registre_de_noms_de_domaine) gérant les extensions de domaines prises.
{{% /notice %}}
