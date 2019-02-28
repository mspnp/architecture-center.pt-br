---
title: 'CAF: Guia de decisão de consistência de recursos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
description: Saiba mais sobre a consistência de recursos ao planejar migrações do Azure.
author: rotycenh
ms.openlocfilehash: 8170bfd09218a451e086a57e0631b7e567eb2b82
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55900249"
---
# <a name="caf-resource-consistency-decision-guide"></a><span data-ttu-id="fb6c7-103">CAF: Guia de decisão de consistência de recursos</span><span class="sxs-lookup"><span data-stu-id="fb6c7-103">CAF: Resource consistency decision guide</span></span>

<span data-ttu-id="fb6c7-104">O [design de assinatura](../subscriptions/overview.md) do Azure define como organizar seus ativos de nuvem em relação à estrutura geral de sua organização.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-104">Azure [subscription design](../subscriptions/overview.md) defines how you organize your cloud assets in relation to your organization's overall structure.</span></span> <span data-ttu-id="fb6c7-105">Além disso, a integração de seus padrões de gerenciamento de TI existente e as políticas organizacionais dependem de como você pode implantar e organizar os recursos de nuvem dentro de uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-105">In addition, integrating your existing IT management standards and your organizational policies depends on how you deploy and organize cloud resources within a subscription.</span></span>

<span data-ttu-id="fb6c7-106">As ferramentas disponíveis para implementar seus designs de implantação, o agrupamento e o gerenciamento de recursos variam por plataforma de nuvem.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-106">The tools available to implement your resource deployment, grouping, and management designs vary by cloud platform.</span></span> <span data-ttu-id="fb6c7-107">Em geral, cada solução inclui os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="fb6c7-107">In general, each solution includes the following features:</span></span>

- <span data-ttu-id="fb6c7-108">Um mecanismo de agrupamento lógico abaixo do nível de assinatura ou conta.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-108">A logical grouping mechanism below the subscription or account level.</span></span>
- <span data-ttu-id="fb6c7-109">A capacidade de implantar recursos por meio de programação com APIs.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-109">The ability to deploy resources programmatically with APIs.</span></span>
- <span data-ttu-id="fb6c7-110">Modelos para criação de implantações padronizadas.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-110">Templates for creating standardized deployments.</span></span>
- <span data-ttu-id="fb6c7-111">A capacidade de implantar as regras de política na assinatura, a conta e os níveis de agrupamento de recursos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-111">The ability to deploy policy rules at the subscription, account, and resource grouping levels.</span></span>

![Opções de consistência de recurso de plotagem da menos para a maix complexa, alinhadas aos links de salto abaixo](../../_images/discovery-guides/discovery-guide-resource-consistency.png)

<span data-ttu-id="fb6c7-113">Ir para: [Agrupamento básico](#basic-grouping) | [Consistência da implantação](#deployment-consistency) | [Consistência de política](#policy-consistency) | [Consistência hierárquica](#hierarchical-consistency) | [Consistência automatizada](#automated-consistency)</span><span class="sxs-lookup"><span data-stu-id="fb6c7-113">Jump to: [Basic grouping](#basic-grouping) | [Deployment consistency](#deployment-consistency) | [Policy consistency](#policy-consistency) | [Hierarchical consistency](#hierarchical-consistency) | [Automated consistency](#automated-consistency)</span></span>

<span data-ttu-id="fb6c7-114">Decisões de implantação e agrupamento de recursos são principalmente conduzidas por estes fatores: tamanho após a migração de estado digital, negócios ou complexidade ambiental que não se adequam dentro de suas abordagens de design de assinatura existente ou a necessidade de impor governança ao longo do tempo após a implantação dos recursos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-114">Resource deployment and grouping decisions are primarily driven by these factors: post-migration digital estate size, business or environmental complexity that doesn't fit neatly within your existing subscription design approaches, or the need to enforce governance over time after resources have been deployed.</span></span> <span data-ttu-id="fb6c7-115">Designs de agrupamento de recursos mais avançados exigem um maior esforço para garantir o agrupamento preciso e isso resulta em um aumento no tempo gasto no gerenciamento de alterações e acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-115">More advanced resource grouping designs require an increased effort to ensure accurate grouping, and this results in an increase in the time spent on change management and tracking.</span></span>

## <a name="basic-grouping"></a><span data-ttu-id="fb6c7-116">Agrupamento básico</span><span class="sxs-lookup"><span data-stu-id="fb6c7-116">Basic grouping</span></span>

<span data-ttu-id="fb6c7-117">No Azure, [grupos de recursos](/azure/azure-resource-manager/resource-group-overview#resource-groups) são um mecanismo de organização de recursos de núcleo para agrupar logicamente os recursos dentro de uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-117">In Azure, [resource groups](/azure/azure-resource-manager/resource-group-overview#resource-groups) are a core resource organization mechanism to logically group resources within a subscription.</span></span>

<span data-ttu-id="fb6c7-118">Os grupos de recursos atuam como contêineres para recursos com um ciclo de vida comum ou restrições de gerenciamento compartilhadas como política ou requisitos de controle de acesso a função (RBAC).</span><span class="sxs-lookup"><span data-stu-id="fb6c7-118">Resource groups act as containers for resources with a common lifecycle or shared management constraints such as policy or role-based access control (RBAC) requirements.</span></span> <span data-ttu-id="fb6c7-119">Os grupos de recursos não podem ser aninhados e os recursos podem pertencer apenas a um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-119">Resource groups can't be nested, and resources can only belong to one resource group.</span></span> <span data-ttu-id="fb6c7-120">Algumas ações podem agir em todos os recursos em um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-120">Some actions can act on all resources in a resource group.</span></span> <span data-ttu-id="fb6c7-121">Por exemplo, a exclusão de um grupo de recursos remove todos os recursos daquele grupo.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-121">For example, deleting a resource group removes all resources within that group.</span></span> <span data-ttu-id="fb6c7-122">Existem padrões comuns durante a criação de grupos de recursos, normalmente são divididos em duas categorias:</span><span class="sxs-lookup"><span data-stu-id="fb6c7-122">There are common patterns when creating resource groups, commonly divided into two categories:</span></span>

- <span data-ttu-id="fb6c7-123">Cargas de trabalho de TI tradicionais: Geralmente, agrupadas por itens no mesmo ciclo de vida, como um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-123">Traditional IT workloads: Most often grouped by items within the same lifecycle, such as an application.</span></span> <span data-ttu-id="fb6c7-124">O agrupamento por aplicativo permite o gerenciamento individual de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-124">Grouping by application allows for individual application management.</span></span>
- <span data-ttu-id="fb6c7-125">As cargas de trabalho TI da Agile: Tendem a se concentrar nos aplicativos de nuvem voltados para o cliente.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-125">Agile IT workloads: Focus on external customer-facing cloud applications.</span></span> <span data-ttu-id="fb6c7-126">Esses grupos de recursos muitas vezes refletem as camadas da implantação (como camada da Web ou camada de aplicativo) e gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-126">These resource groups often reflect the functional layers of deployment (such as web tier or app tier) and management.</span></span>

## <a name="deployment-consistency"></a><span data-ttu-id="fb6c7-127">Consistência de implantação</span><span class="sxs-lookup"><span data-stu-id="fb6c7-127">Deployment consistency</span></span>

<span data-ttu-id="fb6c7-128">Ao criar sobre o mecanismo de agrupamento de recurso base, a maioria das plataformas de nuvem fornecem um sistema para usar os modelos para implantar seus recursos no ambiente de nuvem.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-128">Building on top of the base resource grouping mechanism, most cloud platforms provide a system for using templates to deploy your resources to the cloud environment.</span></span> <span data-ttu-id="fb6c7-129">Você pode usar modelos para criar organização consistente e convenções de nomenclatura ao implantar cargas de trabalho, impor esses aspectos do seu design de implantação e gerenciamento de recursos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-129">You can use templates to create consistent organization and naming conventions when deploying workloads, enforcing those aspects of your resource deployment and management design.</span></span>

<span data-ttu-id="fb6c7-130">Os [Modelos do Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview#template-deployment) permitem que você implante repetidamente seus recursos em um estado consistente usando uma estrutura de grupo de recursos e configuração predeterminada.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-130">[Azure Resource Manager templates](/azure/azure-resource-manager/resource-group-overview#template-deployment) allow you to repeatedly deploy your resources in a consistent state using a predetermined configuration and resource group structure.</span></span> <span data-ttu-id="fb6c7-131">Modelos do Gerenciador de Recursos ajudam a definir um conjunto de padrões como base para suas implantações.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-131">Resource Manager templates help you define a set of standards as a basis for your deployments.</span></span>

<span data-ttu-id="fb6c7-132">Por exemplo, você pode ter um modelo padrão para a implantação de uma carga de trabalho de servidor web que contém duas máquinas virtuais como servidores web combinados com um balanceador de carga para gerenciar o tráfego entre os servidores.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-132">For example, you can have a standard template for deploying a web server workload that contains two virtual machines as web servers combined with a load balancer to manage traffic between the servers.</span></span> <span data-ttu-id="fb6c7-133">Em seguida, você pode reutilizar este modelo para criar implantações estruturalmente idênticas, sempre que uma nova carga de trabalho de servidor de web for necessária, apenas alterar o nome da implantação e endereços IP envolvidos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-133">You can then reuse this template to create structurally identical deployments whenever a new web server workload is needed, only changing the deployment name and IP addresses involved.</span></span>

<span data-ttu-id="fb6c7-134">Observe que você pode implantar esses modelos e integrá-los aos seus sistemas de CI/CD também por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-134">Note that you can also programmatically deploy these templates and integrate them with your CI/CD systems.</span></span>

## <a name="policy-consistency"></a><span data-ttu-id="fb6c7-135">Consistência de política</span><span class="sxs-lookup"><span data-stu-id="fb6c7-135">Policy consistency</span></span>

<span data-ttu-id="fb6c7-136">Para garantir que as políticas de controle sejam aplicadas quando os recursos são criados, a parte do design de agrupamento de recursos envolve o uso de uma configuração comum ao implantar recursos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-136">To ensure that governance policies are applied when resources are created, part of resource grouping design involves using a common configuration when deploying resources.</span></span>

<span data-ttu-id="fb6c7-137">Ao combinar grupos de recursos e modelos padronizados do Gerenciador de Recursos, você pode impor padrões para quais configurações são necessárias em uma implantação e quais regras da [política do Azure](/azure/governance/policy/overview) são aplicadas a cada grupo de recursos ou recurso.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-137">By combining resource groups and standardized Resource Manager templates, you can enforce standards for what settings are required in a deployment and what [Azure Policy](/azure/governance/policy/overview) rules are applied to each resource group or resource.</span></span>

<span data-ttu-id="fb6c7-138">Por exemplo, você pode ter um requisito de que todas as máquinas virtuais implantadas dentro de sua assinatura se conectam a uma sub-rede comum gerenciada por sua equipe de TI central.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-138">For example, you may have a requirement that all virtual machines deployed within your subscription connect to a common subnet managed by your central IT team.</span></span> <span data-ttu-id="fb6c7-139">Você pode criar um modelo padrão para a implantação de VMs de carga de trabalho que criariam um grupo de recursos separado para a carga de trabalho e implantaria as VMs necessárias de lá.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-139">You can create a standard template for deploying workload VMs which would create a separate resource group for the workload and deploy the required VMs there.</span></span> <span data-ttu-id="fb6c7-140">Esse grupo de recursos teria uma regra de política para permitir que somente as interfaces de rede dentro do grupo de recursos fossem associados à sub-rede compartilhada.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-140">This resource group would have a policy rule to only allow network interfaces within the resource group to be joined to the shared subnet.</span></span>

<span data-ttu-id="fb6c7-141">Para obter uma discussão mais detalhada sobre impor suas decisões de política dentro de uma implantação de nuvem, consulte [Imposição de política](../policy-enforcement/overview.md).</span><span class="sxs-lookup"><span data-stu-id="fb6c7-141">For a more in-depth discussion of enforcing your policy decisions within a cloud deployment, see [Policy enforcement](../policy-enforcement/overview.md).</span></span>

## <a name="hierarchical-consistency"></a><span data-ttu-id="fb6c7-142">Consistência hierárquica</span><span class="sxs-lookup"><span data-stu-id="fb6c7-142">Hierarchical consistency</span></span>

<span data-ttu-id="fb6c7-143">À medida que aumenta o tamanho do seu acervo de nuvem, você precisa dar suporte aos mais complicados requisitos de governança que podem ter suporte usando a hierarquia de empresa/departamento/conta/assinatura do Contrato Enterprise do Azure.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-143">As the size of your cloud estate grows, you may need to support more complicated governance requirements than can be supported using the Azure Enterprise Agreement's Enterprise/Department/Account/Subscription hierarchy.</span></span> <span data-ttu-id="fb6c7-144">Grupos de recursos permitem que você dê suporte a níveis adicionais de hierarquia em sua organização, aplicando regras de política do Azure e controles de acesso em um nível de grupo de recurso.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-144">Resource groups allows you to support additional levels of hierarchy within your organization, applying Azure Policy rules and access controls at a resource group level.</span></span>

<span data-ttu-id="fb6c7-145">[Grupos de gerenciamento do Azure](../subscriptions/overview.md#management-groups) podem dar suporte a estruturas organizacionais mais complicadas sobrepondo uma hierarquia alternativa na parte superior da estrutura do seu contrato enterprise.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-145">[Azure management groups](../subscriptions/overview.md#management-groups) can support more complicated organizational structures by overlaying an alternative hierarchy on top of your enterprise agreement's structure.</span></span> <span data-ttu-id="fb6c7-146">Isso permite assinaturas e recursos que eles contêm, para dar suporte ao controle de acesso e mecanismos de imposição de política organizados para corresponder com os seus requisitos organizacionais comerciais.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-146">This allows subscriptions, and the resources they contain, to support access control and policy enforcement mechanisms organized to match your business organizational requirements.</span></span>

## <a name="automated-consistency"></a><span data-ttu-id="fb6c7-147">Consistência automatizada</span><span class="sxs-lookup"><span data-stu-id="fb6c7-147">Automated consistency</span></span>

<span data-ttu-id="fb6c7-148">Para implantações de nuvem grande, a governança global se torna mais importante e mais complexa.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-148">For large cloud deployments, global governance becomes both more important and more complex.</span></span> <span data-ttu-id="fb6c7-149">É crucial aplicar e impor requisitos de governança ao implantar recursos automaticamente, bem como atender aos requisitos atualizados para implantações existentes.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-149">It is crucial to automatically apply and enforce governance requirements when deploying resources, as well as meet updated requirements for existing deployments.</span></span>

<span data-ttu-id="fb6c7-150">[Azure Blueprints](/azure/governance/blueprints/overview) permitem que as organizações deem suporte à governança global de instalações de nuvem grande no Azure.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-150">[Azure Blueprints](/azure/governance/blueprints/overview) enable organizations to support global governance of large cloud estates in Azure.</span></span> <span data-ttu-id="fb6c7-151">Blueprints se movem além dos recursos fornecidos pelos modelos padrão do Azure Resource Manager para criar orquestrações de implantação completa capaz de recursos de implantação e aplicar regras de política.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-151">Blueprints move beyond the capabilities provided by standard Azure Resource Manager templates to create complete deployment orchestrations capable of deploying resources and applying policy rules.</span></span> <span data-ttu-id="fb6c7-152">Blueprints oferecem suporte a controle de versão, a capacidade aplicar as atualizações para todas as assinaturas em que o plano gráfico foi usado e a capacidade de bloquear assinaturas implantadas para evitar a criação não autorizada e a modificação dos recursos.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-152">Blueprints supports versioning, the ability to make apply updates to all subscriptions where the blueprint was used, and the ability to lock down deployed subscriptions to avoid the unauthorized creation and modification of resources.</span></span>

<span data-ttu-id="fb6c7-153">Esses pacotes permitem que as equipes de TI e de desenvolvimento implantem rapidamente novas cargas de trabalho e ativos de rede que estejam em conformidade com a alteração dos requisitos de política organizacional.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-153">These deployment packages allow IT and development teams to rapidly deploy new workloads and networking assets that comply with changing organizational policy requirements.</span></span> <span data-ttu-id="fb6c7-154">Os blueprints podem ser integrados em pipelines de CI/CD para aplicar os padrões de governança revisados para implantações conforme são atualizados.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-154">Blueprints can also be integrated into CI/CD pipelines to apply revised governance standards to deployments as they are updated.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fb6c7-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="fb6c7-155">Next steps</span></span>

<span data-ttu-id="fb6c7-156">Saiba como os recursos de nomenclatura e marcação são usados para organizar e gerenciar seus recursos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="fb6c7-156">Learn how resource naming and tagging are used to further organize and manage your cloud resources.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb6c7-157">Recursos de nomenclatura e marcação</span><span class="sxs-lookup"><span data-stu-id="fb6c7-157">Resource naming and tagging</span></span>](../resource-tagging/overview.md)