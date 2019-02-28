---
title: 'CAF: Empresa de grande porte – evolução da linha de base de identidade'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
description: Empresa de grande porte – evolução da linha de base de identidade
author: BrianBlanchard
ms.openlocfilehash: efda14819bfbc70632dc9bb8b4c6c5aca96004c0
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55900256"
---
# <a name="large-enterprise-identity-baseline-evolution"></a><span data-ttu-id="abecc-103">Empresas de grande porte: Evolução da linha de base de identidade</span><span class="sxs-lookup"><span data-stu-id="abecc-103">Large enterprise: Identity Baseline evolution</span></span>

<span data-ttu-id="abecc-104">Este artigo desenvolve a narrativa adicionando controles de Linha de Base de identidade para a governança MVP.</span><span class="sxs-lookup"><span data-stu-id="abecc-104">This article evolves the narrative by adding Identity Baseline controls to the governance MVP.</span></span>

## <a name="evolution-of-the-narrative"></a><span data-ttu-id="abecc-105">Evolução da narrativa</span><span class="sxs-lookup"><span data-stu-id="abecc-105">Evolution of the narrative</span></span>

<span data-ttu-id="abecc-106">A justificativa comercial para a migração de nuvem dos dois datacenters foi aprovada pelo CFO.</span><span class="sxs-lookup"><span data-stu-id="abecc-106">The business justification for the cloud migration of the two datacenters was approved by the CFO.</span></span> <span data-ttu-id="abecc-107">Durante o estudo da viabilidade técnica, várias dificuldades foram descobertas:</span><span class="sxs-lookup"><span data-stu-id="abecc-107">During the technical feasibility study, several roadblocks were discovered:</span></span>

- <span data-ttu-id="abecc-108">Dados protegidos e aplicativos de missão crítica representam 25% das cargas de trabalho em dois data centers.</span><span class="sxs-lookup"><span data-stu-id="abecc-108">Protected data and mission-critical applications represent 25% of the workloads in the two datacenters.</span></span> <span data-ttu-id="abecc-109">Nenhum dos dois pode ser eliminado até que as políticas de controle atual em relação à PII e aplicativos de missão crítica tenham sido modernizados.</span><span class="sxs-lookup"><span data-stu-id="abecc-109">Neither can be eliminated until the current governance policies regarding PII and mission-critical applications have been modernized.</span></span>
- <span data-ttu-id="abecc-110">% 7 dos ativos nos data centers não são compatíveis com a nuvem.</span><span class="sxs-lookup"><span data-stu-id="abecc-110">7% of the assets in those datacenters are not cloud-compatible.</span></span> <span data-ttu-id="abecc-111">Eles serão movidos para um datacenter alternativo antes do término do contrato de datacenter.</span><span class="sxs-lookup"><span data-stu-id="abecc-111">They will be moved to an alternate datacenter before termination of the datacenter contract.</span></span>
- <span data-ttu-id="abecc-112">15% dos ativos no data center (750 máquinas de virtuais) têm uma dependência na autenticação herdada ou autenticação de multifator de terceiros.</span><span class="sxs-lookup"><span data-stu-id="abecc-112">15% of the assets in the datacenter (750 virtual machines) have a dependency on legacy authentication or third-party multi-factor authentication.</span></span>
- <span data-ttu-id="abecc-113">A conexão VPN que conecta os datacenters existentes e o Azure não oferece velocidades ou latência de transmissão de dados suficientes para migrar o volume dos ativos dentro da linha do tempo de dois para desativar o datacenter.</span><span class="sxs-lookup"><span data-stu-id="abecc-113">The VPN connection that connects existing datacenters and Azure does not offer sufficient data transmission speeds or latency to migrate the volume of assets within the two-year timeline to retire the datacenter.</span></span>

<span data-ttu-id="abecc-114">Os dois primeiros obstáculos estão sendo reduzidos em paralelo.</span><span class="sxs-lookup"><span data-stu-id="abecc-114">The first two roadblocks are being mitigated in parallel.</span></span> <span data-ttu-id="abecc-115">Este artigo abordará a resolução das dificuldades do terceiro e quarto bloqueio.</span><span class="sxs-lookup"><span data-stu-id="abecc-115">This article will address the resolution of the third and fourth roadblocks.</span></span>

### <a name="evolution-of-the-cloud-governance-team"></a><span data-ttu-id="abecc-116">Evolução da equipe de Governança de Nuvem</span><span class="sxs-lookup"><span data-stu-id="abecc-116">Evolution of the Cloud Governance team</span></span>

<span data-ttu-id="abecc-117">A Equipe de Governança de Nuvem está aumentando.</span><span class="sxs-lookup"><span data-stu-id="abecc-117">The Cloud Governance team is expanding.</span></span> <span data-ttu-id="abecc-118">Dada a necessidade de suporte adicionais sobre o gerenciamento de identidade, um administrador de sistemas da equipe de linha de base de identidade agora participa de uma reunião semanal para manter os membros da equipe existente ciente das alterações.</span><span class="sxs-lookup"><span data-stu-id="abecc-118">Given the need for additional support regarding identity management, a systems administrator from the Identity Baseline team now participates in a weekly meeting to keep the existing team members aware of changes.</span></span>

### <a name="evolution-of-the-current-state"></a><span data-ttu-id="abecc-119">Evolução do estado atual</span><span class="sxs-lookup"><span data-stu-id="abecc-119">Evolution of the current state</span></span>

<span data-ttu-id="abecc-120">A equipe de TI tem aprovação para prosseguir com o CIO e o CFO planeja desativar dois data centers.</span><span class="sxs-lookup"><span data-stu-id="abecc-120">The IT team has approval to move forward with the CIO and CFO's plans to retire two datacenters.</span></span> <span data-ttu-id="abecc-121">No entanto, a IT está preocupada que 750 (15%) dos ativos nos data centers terão de ser movidos em algum lugar diferente da nuvem.</span><span class="sxs-lookup"><span data-stu-id="abecc-121">However, IT is concerned that 750 (15%) of the assets in those datacenters will have to be moved somewhere other than the cloud.</span></span>

### <a name="evolution-of-the-future-state"></a><span data-ttu-id="abecc-122">Evolução do estado futuro</span><span class="sxs-lookup"><span data-stu-id="abecc-122">Evolution of the future state</span></span>

<span data-ttu-id="abecc-123">Os novos planos de estado futuro exigem uma solução de identidade da linha de base mais robusta para migrar as 750 máquinas virtuais com os requisitos de autenticação herdados.</span><span class="sxs-lookup"><span data-stu-id="abecc-123">The new future state plans require a more robust Identity Baseline solution to migrate the 750 virtual machines with legacy authentication requirements.</span></span> <span data-ttu-id="abecc-124">Além desses dois data centers, porcentagens semelhantes de ativos em outros data centers devem ser afetadas por esse desafio.</span><span class="sxs-lookup"><span data-stu-id="abecc-124">Beyond these two datacenters, similar percentages of assets in other datacenters are expected to be affected by this challenge.</span></span>
<span data-ttu-id="abecc-125">O estado futuro agora também requer uma conexão do provedor de nuvem à solução MPLS/baseado em linha da empresa.</span><span class="sxs-lookup"><span data-stu-id="abecc-125">The future state now also requires a connection from the cloud provider to the company’s MPLS/leased-line solution.</span></span>

<span data-ttu-id="abecc-126">As alterações ao estado atual e futuro expõem novos riscos que exigem novas instruções de política.</span><span class="sxs-lookup"><span data-stu-id="abecc-126">The changes to current and future state expose new risks that will require new policy statements.</span></span>

## <a name="evolution-of-tangible-risks"></a><span data-ttu-id="abecc-127">Evolução de riscos tangíveis</span><span class="sxs-lookup"><span data-stu-id="abecc-127">Evolution of tangible risks</span></span>

<span data-ttu-id="abecc-128">**Interrupção dos negócios durante a migração**.</span><span class="sxs-lookup"><span data-stu-id="abecc-128">**Business interruption during migration**.</span></span> <span data-ttu-id="abecc-129">A migração para a nuvem cria um risco controlado e limite de tempo que pode ser gerenciado.</span><span class="sxs-lookup"><span data-stu-id="abecc-129">Migration to the cloud creates a controlled, time-bound risk that can be managed.</span></span> <span data-ttu-id="abecc-130">Mover o hardware de classificação por vencimento para outra parte do mundo é um risco muito maior.</span><span class="sxs-lookup"><span data-stu-id="abecc-130">Moving aging hardware to another part of the world is much higher risk.</span></span> <span data-ttu-id="abecc-131">Uma estratégia de mitigação é necessária para evitar interrupções para as operações de negócios.</span><span class="sxs-lookup"><span data-stu-id="abecc-131">A mitigation strategy is needed to avoid interruptions to business operations.</span></span>

<span data-ttu-id="abecc-132">**Dependências de identidade existentes**.</span><span class="sxs-lookup"><span data-stu-id="abecc-132">**Existing identity dependencies**.</span></span> <span data-ttu-id="abecc-133">As dependências em serviços de autenticação e identidade existentes podem atrasar ou evitar a migração de algumas cargas de trabalho para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="abecc-133">Dependencies on existing authentication and identity services may delay or prevent the migration of some workloads to the cloud.</span></span> <span data-ttu-id="abecc-134">A falha ao retornar dois datacenters na hora incorrerá em milhões de dólares em valores de concessão de datacenter.</span><span class="sxs-lookup"><span data-stu-id="abecc-134">Failure to return the two datacenters on time will incur millions of dollars in datacenter lease fees.</span></span>

<span data-ttu-id="abecc-135">Esse risco de negócios pode ser dividido em alguns riscos técnicos:</span><span class="sxs-lookup"><span data-stu-id="abecc-135">This business risk can be expanded into a few technical risks:</span></span>

- <span data-ttu-id="abecc-136">A autenticação herdada pode não estar disponível na nuvem, limitando a implantação de alguns aplicativos.</span><span class="sxs-lookup"><span data-stu-id="abecc-136">Legacy authentication might not be available in the cloud, limiting deployment of some applications.</span></span>
- <span data-ttu-id="abecc-137">A solução MFA de terceiros atual pode não estar disponível na nuvem, limitando a implantação de alguns aplicativos.</span><span class="sxs-lookup"><span data-stu-id="abecc-137">The current third-party MFA solution might not be available in the cloud, limiting deployment of some applications.</span></span>
- <span data-ttu-id="abecc-138">Reorganizar ou mover a nuvem cria resultados e adiciona custos.</span><span class="sxs-lookup"><span data-stu-id="abecc-138">Retooling or moving either could create outages and add costs.</span></span>
- <span data-ttu-id="abecc-139">A velocidade e a estabilidade do VPN podem impedir a migração.</span><span class="sxs-lookup"><span data-stu-id="abecc-139">The speed and stability of the VPN might impede migration.</span></span>
- <span data-ttu-id="abecc-140">O tráfego de entrada para a nuvem pode causar problemas de segurança em outras partes da rede global.</span><span class="sxs-lookup"><span data-stu-id="abecc-140">Traffic coming into the cloud could cause security issues in other parts of the global network.</span></span>

## <a name="evolution-of-the-policy-statements"></a><span data-ttu-id="abecc-141">Evolução das instruções da política</span><span class="sxs-lookup"><span data-stu-id="abecc-141">Evolution of the policy statements</span></span>

<span data-ttu-id="abecc-142">As seguintes alterações à política ajudam a reduzir novos riscos e a orientar a implementação.</span><span class="sxs-lookup"><span data-stu-id="abecc-142">The following changes to policy will help mitigate the new risks and guide implementation.</span></span>

1. <span data-ttu-id="abecc-143">O provedor de nuvem escolhido deve oferecer um meio de autenticar por meio de métodos herdados.</span><span class="sxs-lookup"><span data-stu-id="abecc-143">The chosen cloud provider must offer a means of authenticating via legacy methods.</span></span>
2. <span data-ttu-id="abecc-144">O provedor de nuvem escolhido deve oferecer um meio de autenticação com a solução atual de MFA de terceiros.</span><span class="sxs-lookup"><span data-stu-id="abecc-144">The chosen cloud provider must offer a means of authentication with the current third-party MFA solution.</span></span>
3. <span data-ttu-id="abecc-145">Uma conexão privada de alta velocidade deve ser estabelecida entre o provedor de nuvem e o provedor de telecomunicações da empresa, conectando o provedor de nuvem à rede global dos datacenters.</span><span class="sxs-lookup"><span data-stu-id="abecc-145">A high-speed private connection should be established between the cloud provider and the company’s telco provider, connecting the cloud provider to the global network of datacenters.</span></span>
4. <span data-ttu-id="abecc-146">Até que os requisitos de segurança suficientes sejam estabelecidos, nenhum tráfego de entrada público pode acessar os ativos da empresa hospedados na nuvem.</span><span class="sxs-lookup"><span data-stu-id="abecc-146">Until sufficient security requirements are established, no inbound public traffic may access company assets hosted in the cloud.</span></span> <span data-ttu-id="abecc-147">Todas as portas são bloqueadas de qualquer fonte fora da WAN global.</span><span class="sxs-lookup"><span data-stu-id="abecc-147">All ports are blocked from any source outside of the global WAN.</span></span>

## <a name="evolution-of-the-best-practices"></a><span data-ttu-id="abecc-148">Evolução das práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="abecc-148">Evolution of the best practices</span></span>

<span data-ttu-id="abecc-149">O design de MVP de governança evoluirá para incluir novas políticas do Azure e uma implementação do Active Directory Domain Services em uma máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="abecc-149">The governance MVP design evolves to include new Azure policies and an implementation of Active Directory on a virtual machine.</span></span> <span data-ttu-id="abecc-150">Juntas, essas duas alterações de design atenderão às novas instruções da política corporativa.</span><span class="sxs-lookup"><span data-stu-id="abecc-150">Together, these two design changes fulfill the new corporate policy statements.</span></span>

<span data-ttu-id="abecc-151">Aqui estão as novas práticas recomendadas:</span><span class="sxs-lookup"><span data-stu-id="abecc-151">Here are the new best practices:</span></span>

1. <span data-ttu-id="abecc-152">Blueprint DMZ: O lado local do DMZ deve ser configurado para permitir comunicação entre a seguinte solução e os servidores do Active Directory Domain Services local.</span><span class="sxs-lookup"><span data-stu-id="abecc-152">DMZ blueprint: The on-premises side of the DMZ should be configured to allow communication between the following solution and the on-premises Active Directory servers.</span></span> <span data-ttu-id="abecc-153">Essa prática recomendada requer um DMZ para habilitar o Active Directory Domain Services entre os limites de rede.</span><span class="sxs-lookup"><span data-stu-id="abecc-153">This best practice requires a DMZ to enable Active Directory Domain Services across network boundaries.</span></span>
2. <span data-ttu-id="abecc-154">Modelos do Azure Resource Manager:</span><span class="sxs-lookup"><span data-stu-id="abecc-154">Azure Resource Manager templates:</span></span>
    1. <span data-ttu-id="abecc-155">Defina um NSG para bloquear o tráfego externo e o tráfego interno da lista de permissões.</span><span class="sxs-lookup"><span data-stu-id="abecc-155">Define an NSG to block external traffic and whitelist internal traffic.</span></span>
    1. <span data-ttu-id="abecc-156">Implante duas máquinas virtuais do AD em um par com balanceamento de carga com base em uma imagem dourada.</span><span class="sxs-lookup"><span data-stu-id="abecc-156">Deploy two AD virtual machines in a load balanced pair based on a golden image.</span></span> <span data-ttu-id="abecc-157">Na primeira inicialização, essa imagem executa um script do PowerShell para ingressar no domínio e registrar-se aos serviços de domínio.</span><span class="sxs-lookup"><span data-stu-id="abecc-157">On first boot, that image runs a PowerShell script to join the domain and register with domain services.</span></span> <span data-ttu-id="abecc-158">Para obter mais informações, consulte [Estendendo o Active Directory Domain Services (AD DS) para o Azure](../../../../reference-architectures/identity/adds-extend-domain.md).</span><span class="sxs-lookup"><span data-stu-id="abecc-158">For more information, see [Extend Active Directory Domain Services (AD DS) to Azure](../../../../reference-architectures/identity/adds-extend-domain.md).</span></span>
3. <span data-ttu-id="abecc-159">Azure Policy: Aplica o NSG a todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="abecc-159">Azure Policy: Apply the NSG to all resources.</span></span>
4. <span data-ttu-id="abecc-160">Blueprint do Azure</span><span class="sxs-lookup"><span data-stu-id="abecc-160">Azure blueprint</span></span>
    1. <span data-ttu-id="abecc-161">Criar um blueprint nomeado `active-directory-virtual-machines`.</span><span class="sxs-lookup"><span data-stu-id="abecc-161">Create a blueprint named `active-directory-virtual-machines`.</span></span>
    1. <span data-ttu-id="abecc-162">Adicione cada um dos modelos do AD e as políticas para o blueprint.</span><span class="sxs-lookup"><span data-stu-id="abecc-162">Add each of the AD templates and policies to the blueprint.</span></span>
    1. <span data-ttu-id="abecc-163">Publique o plano gráfico em qualquer grupo de gerenciamento aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="abecc-163">Publish the blueprint to any applicable management group.</span></span>
    1. <span data-ttu-id="abecc-164">Aplique o blueprint para qualquer assinatura que exija autenticação de MFA de terceiros ou herdada.</span><span class="sxs-lookup"><span data-stu-id="abecc-164">Apply the blueprint to any subscription requiring legacy or third-party MFA authentication.</span></span>
    1. <span data-ttu-id="abecc-165">A instância do AD em execução no Azure agora pode ser usada como uma extensão do local a solução do AD, permitindo que ele se integre à ferramenta MFA existente e forneçam a autenticação baseada em declarações, ambos por meio da funcionalidade existente do Active Directory Domain Services.</span><span class="sxs-lookup"><span data-stu-id="abecc-165">The instance of AD running in Azure can now be used as an extension of the on-premises AD solution, allowing it to integrate with the existing MFA tool and provide claims-based authentication, both through existing Active Directory functionality.</span></span>

## <a name="conclusion"></a><span data-ttu-id="abecc-166">Conclusão</span><span class="sxs-lookup"><span data-stu-id="abecc-166">Conclusion</span></span>

<span data-ttu-id="abecc-167">Adicionar essas alterações para a governança MVP ajuda a atenuar muitos riscos neste artigo, permitindo que cada equipe de adoção da nuvem se mova rapidamente após esse obstáculo.</span><span class="sxs-lookup"><span data-stu-id="abecc-167">Adding these changes to the governance MVP helps mitigate many of the risks in this article, allowing each cloud adoption team to quickly move past this roadblock.</span></span>

## <a name="next-steps"></a><span data-ttu-id="abecc-168">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="abecc-168">Next steps</span></span>

<span data-ttu-id="abecc-169">Como a adoção da nuvem se desenvolve e entrega valor comercial, riscos e governança de nuvem também precisam evoluir.</span><span class="sxs-lookup"><span data-stu-id="abecc-169">As cloud adoption evolves and delivers additional business value, risks and cloud governance needs will also evolve.</span></span> <span data-ttu-id="abecc-170">A seguir estão algumas evoluções que podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="abecc-170">The following are a few evolutions that may occur.</span></span> <span data-ttu-id="abecc-171">Para a empresa fictícia nessa jornada, o próximo gatilho é a inclusão dos dados protegidos no plano de adoção de nuvem.</span><span class="sxs-lookup"><span data-stu-id="abecc-171">For the fictional company in this journey, the next trigger is the inclusion of protected data in the cloud adoption plan.</span></span> <span data-ttu-id="abecc-172">Essa alteração exigirá os controles de segurança adicional.</span><span class="sxs-lookup"><span data-stu-id="abecc-172">This change will require additional security controls.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="abecc-173">Evolução da Linha de Base de Segurança</span><span class="sxs-lookup"><span data-stu-id="abecc-173">Security Baseline evolution</span></span>](./security-baseline-evolution.md)