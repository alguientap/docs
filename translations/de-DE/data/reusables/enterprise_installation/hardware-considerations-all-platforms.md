- [Minimum requirements](#minimum-requirements)
- [Beta features in {% data variables.product.prodname_ghe_server %} 2.22](#beta-features-in-github-enterprise-server-222)
- [Speicher](#storage)
- [CPU and memory](#cpu-and-memory)

#### Minimum requirements

We recommend different hardware configurations depending on the number of user licenses for {% data variables.product.product_location %}. If you provision more resources than the minimum requirements, your instance will perform and scale better.

{% data reusables.enterprise_installation.hardware-rec-table %}{% if currentVersion == "enterprise-server@2.22" or currentVersion == "github-ae@latest" %} If you enable the beta for {% data variables.product.prodname_actions %}, review the following requirements and recommendations.

- You must configure at least one runner for {% data variables.product.prodname_actions %} workflows. Weitere Informationen findest Du unter „[Informationen zu selbst-gehosteten Runnern](/actions/hosting-your-own-runners/about-self-hosted-runners)“.
- You must configure external blob storage. For more information, see "[Enabling {% data variables.product.prodname_actions %} and configuring storage](/enterprise/admin/github-actions/enabling-github-actions-and-configuring-storage)."
- You may need to configure additional CPU and memory resources. The additional resources you need to provision for {% data variables.product.prodname_actions %} depend on the number of workflows your users run concurrently, and the overall levels of activity for users, automations, and integrations.

    | Maximum jobs per minute | Additional vCPUs | Additional memory |
    |:----------------------- | ----------------:| -----------------:|
    | Light testing           |                4 |           30.5 GB |
    | 25                      |                8 |             61 GB |
    | 35                      |               16 |            122 GB |
    | 100                     |               32 |            244 GB |

{% endif %}

#### Speicher

We recommend a high-performance SSD with high input/output operations per second (IOPS) and low latency for {% data variables.product.prodname_ghe_server %}. Workloads are I/O intensive. If you use a bare metal hypervisor, we recommend directly attaching the disk or using a disk from a storage area network (SAN).

Your instance requires a persistent data disk separate from the root disk. Weitere Informationen findest Du unter „[Systemübersicht](/enterprise/admin/guides/installation/system-overview)“.

{% if currentVersion ver_gt "enterprise-server@2.21" or currentVersion == "github-ae@latest" %}

If you enable the beta of {% data variables.product.prodname_actions %} in {% data variables.product.prodname_ghe_server %} 2.22, you'll need to configure external blob storage. For more information, see "[Enabling {% data variables.product.prodname_actions %} and configuring storage](/enterprise/admin/github-actions/enabling-github-actions-and-configuring-storage)."

{% endif %}

You can resize your instance's root disk by building a new instance or using an existing instance. Weitere Informationen findest Du unter „[Speicherkapazität erhöhen](/enterprise/{{ currentVersion }}/admin/guides/installation/increasing-storage-capacity)“.

#### CPU and memory

{% data variables.product.prodname_ghe_server %} requires more CPU and memory resources depending on levels of activity for users, automations, and integrations.

{% data reusables.enterprise_installation.increasing-cpus-req %}

{% warning %}

**Warning:** We recommend that users configure webhook events to notify external systems of activity on {% data variables.product.prodname_ghe_server %}. Automated checks for changes, or _polling_, will negatively impact the performance and scalability of your instance. For more information, see "[About webhooks](/github/extending-github/about-webhooks)."

{% endwarning %}

You can increase your instance's CPU or memory resources. For more information, see "[Increasing CPU or memory resources](/enterprise/admin/installation/increasing-cpu-or-memory-resources).
