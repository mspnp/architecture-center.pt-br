---
title: 'CAF: Métricas de Aceleração de Implantação, indicadores e tolerância a riscos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
description: Métricas de Aceleração de Implantação, indicadores e tolerância a riscos
author: alexbuckgit
ms.openlocfilehash: 87d6f9f67b98d5761aced560392c9d38fa682ee7
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55900251"
---
# <a name="deployment-acceleration-metrics-indicators-and-risk-tolerance"></a><span data-ttu-id="46ae7-103">Métricas de Aceleração de Implantação, indicadores e tolerância a riscos</span><span class="sxs-lookup"><span data-stu-id="46ae7-103">Deployment Acceleration metrics, indicators, and risk tolerance</span></span>

<span data-ttu-id="46ae7-104">Este artigo tem como objetivo ajudar a quantificar a tolerância a riscos do negócios no que diz respeito à Aceleração de Implantação.</span><span class="sxs-lookup"><span data-stu-id="46ae7-104">This article is intended to help you quantify business risk tolerance as it relates to Deployment Acceleration.</span></span> <span data-ttu-id="46ae7-105">Definir métricas e indicadores ajuda a criar um caso de negócios para fazer um investimento no amadurecimento da disciplina de Aceleração de Implantação.</span><span class="sxs-lookup"><span data-stu-id="46ae7-105">Defining metrics and indicators helps you create a business case for making an investment in the maturity of the Deployment Acceleration discipline.</span></span>

## <a name="metrics"></a><span data-ttu-id="46ae7-106">Métricas</span><span class="sxs-lookup"><span data-stu-id="46ae7-106">Metrics</span></span>

<span data-ttu-id="46ae7-107">A Aceleração de Implantação se concentra na implantação, atualização e manutenção de recursos de nuvem configurados para a operação de sistemas adequados.</span><span class="sxs-lookup"><span data-stu-id="46ae7-107">Deployment Acceleration focuses on deploying, updating, and maintaining cloud resources configured for proper systems operation.</span></span> <span data-ttu-id="46ae7-108">As informações a seguir são úteis ao adotar essa disciplina de governança de nuvem:</span><span class="sxs-lookup"><span data-stu-id="46ae7-108">The following information is useful when adopting this discipline of cloud governance:</span></span>

- <span data-ttu-id="46ae7-109">**Objetivo de Tempo de Recuperação (RTO)**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-109">**Recovery time objective (RTO)**.</span></span> <span data-ttu-id="46ae7-110">Tempo máximo aceitável que um aplicativo pode ficar indisponível após um incidente.</span><span class="sxs-lookup"><span data-stu-id="46ae7-110">The maximum acceptable time that an application can be unavailable after an incident.</span></span>
- <span data-ttu-id="46ae7-111">**Objetivo de Ponto de Recuperação (RPO)**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-111">**Recovery point objective (RPO)**.</span></span> <span data-ttu-id="46ae7-112">Duração máxima de perda de dados que é aceitável durante um desastre.</span><span class="sxs-lookup"><span data-stu-id="46ae7-112">The maximum duration of data loss that is acceptable during a disaster.</span></span> <span data-ttu-id="46ae7-113">Por exemplo, se você armazena dados em um único banco de dados, com nenhuma replicação para outros bancos de dados, e executar backups a cada hora, poderá perder até uma hora de dados.</span><span class="sxs-lookup"><span data-stu-id="46ae7-113">For example, if you store data in a single database, with no replication to other databases, and perform hourly backups, you could lose up to an hour of data.</span></span>
- <span data-ttu-id="46ae7-114">**Tempo Médio de Recuperação (MTTR)**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-114">**Mean time to recover (MTTR)**.</span></span> <span data-ttu-id="46ae7-115">Tempo médio necessário para restaurar um componente após uma falha.</span><span class="sxs-lookup"><span data-stu-id="46ae7-115">The average time required to restore a component after a failure.</span></span>
- <span data-ttu-id="46ae7-116">**Tempo médio entre falhas (MTBF)**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-116">**Mean time between failures (MTBF)**.</span></span> <span data-ttu-id="46ae7-117">A duração de um componente razoável pode esperar para executar entre interrupções.</span><span class="sxs-lookup"><span data-stu-id="46ae7-117">The duration that a component can reasonably expect to run between outages.</span></span> <span data-ttu-id="46ae7-118">Essa métrica pode ajudar você a calcular a frequência com que um serviço ficará indisponível.</span><span class="sxs-lookup"><span data-stu-id="46ae7-118">This metric can help you calculate how often a service will become unavailable.</span></span>
- <span data-ttu-id="46ae7-119">**Contratos de nível de serviço (SLAs)**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-119">**Service level agreements (SLA)**.</span></span> <span data-ttu-id="46ae7-120">Isso pode incluir compromissos da Microsoft para atualização e conectividade dos serviços do Azure, bem como compromissos realizados pela empresa para seus clientes internos e externos.</span><span class="sxs-lookup"><span data-stu-id="46ae7-120">This can include both Microsoft’s commitments for uptime and connectivity of Azure services, as well as commitments made by the business to its external and internal customers.</span></span>
- <span data-ttu-id="46ae7-121">**Tempo de implantação**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-121">**Time to deployment**.</span></span> <span data-ttu-id="46ae7-122">A quantidade de tempo necessária para implantar atualizações em um sistema existente.</span><span class="sxs-lookup"><span data-stu-id="46ae7-122">The amount of time needed to deploy updates to an existing system.</span></span>
- <span data-ttu-id="46ae7-123">**Ativos fora de conformidade**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-123">**Assets out-of-compliance**.</span></span> <span data-ttu-id="46ae7-124">O número ou porcentagem de recursos que estão fora de conformidade com as políticas definidas.</span><span class="sxs-lookup"><span data-stu-id="46ae7-124">The number or percentage of resources that are out of compliance with defined policies.</span></span>

## <a name="risk-tolerance-indicators"></a><span data-ttu-id="46ae7-125">Indicadores de tolerância de risco</span><span class="sxs-lookup"><span data-stu-id="46ae7-125">Risk tolerance indicators</span></span>

<span data-ttu-id="46ae7-126">Os riscos relacionados à aceleração de implantação em grande parte são relacionados ao número e a complexidade dos sistemas baseados em nuvem implantados para sua empresa.</span><span class="sxs-lookup"><span data-stu-id="46ae7-126">Risks related to Deployment Acceleration are largely related to the number and complexity of cloud-based systems deployed for your enterprise.</span></span> <span data-ttu-id="46ae7-127">À medida em que a sua propriedade de nuvem cresce, o número de sistemas implantados e a frequência de atualização dos seus recursos aumentarão.</span><span class="sxs-lookup"><span data-stu-id="46ae7-127">As your cloud estate grows, the number of systems deployed and the frequency of updating your cloud resources will increase.</span></span> <span data-ttu-id="46ae7-128">As dependências entre recursos ampliarão a importância de garantir a configuração adequada de recursos e a criação de sistemas para resiliência se um ou mais recurso apresentar tempo de inatividade inesperado.</span><span class="sxs-lookup"><span data-stu-id="46ae7-128">Dependencies between resources magnify the importance of ensuring proper configuration of resources and designing systems for resiliency if one or more resources experiences unexpected downtime.</span></span>

<!-- "en-us" location is required for the URL below. -->

<span data-ttu-id="46ae7-129">Considere adotar um DEvOps ou cultura organizacional [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) no início de sua jornada de adoção da nuvem.</span><span class="sxs-lookup"><span data-stu-id="46ae7-129">Consider adopting a DevOps or [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) organizational culture early in your cloud adoption journey.</span></span> <span data-ttu-id="46ae7-130">Organizações de TI corporativas tradicionais geralmente têm isolados operações, segurança e equipes de desenvolvimento que muitas vezes não colaboram bem ou são até mesmo antagônicos ou hostis umas com as outras.</span><span class="sxs-lookup"><span data-stu-id="46ae7-130">Traditional corporate IT organizations often have siloed operations, security, and development teams that often do not collaborate well or are even adversarial or hostile towards one another.</span></span> <span data-ttu-id="46ae7-131">Reconhecer esses desafios no início e integrar os principais stakeholders de cada uma das equipes pode ajudar a garantir a agilidade na sua adoção da nuvem permanecendo seguro e bem governado.</span><span class="sxs-lookup"><span data-stu-id="46ae7-131">Recognizing these challenges early and integrating key stakeholders from each of the teams can help ensure agility in your cloud adoption while remaining secure and well-governed.</span></span>

<span data-ttu-id="46ae7-132">Trabalhe com a sua equipe DevSecOps e com os stakeholders da empresa para identificar os [riscos de negócios](business-risks.md) relacionados à configuração, em seguida, determine uma linha de base aceitável para tolerância a riscos de configuração.</span><span class="sxs-lookup"><span data-stu-id="46ae7-132">Work with your DevSecOps team and business stakeholders to identify [business risks](business-risks.md) related to configuration, then determine an acceptable baseline for configuration risk tolerance.</span></span> <span data-ttu-id="46ae7-133">Esta seção de diretrizes de CAF fornece exemplos, mas os riscos e linhas de base detalhados da sua empresa ou das suas implantações podem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="46ae7-133">This section of the CAF guidance provides examples, but the detailed risks and baselines for your company or deployments will likely differ.</span></span>

<span data-ttu-id="46ae7-134">Assim que você tiver uma linha de base, estabeleça parâmetros de comparação mínimos que representem um aumento inaceitável em seus riscos identificados.</span><span class="sxs-lookup"><span data-stu-id="46ae7-134">Once you have a baseline, establish minimum benchmarks representing an unacceptable increase in your identified risks.</span></span> <span data-ttu-id="46ae7-135">Esses parâmetros de comparação atuam como gatilhos quando você precisar tomar medidas para atenuar esses riscos.</span><span class="sxs-lookup"><span data-stu-id="46ae7-135">These benchmarks act as triggers for when you need to take action to mitigate these risks.</span></span> <span data-ttu-id="46ae7-136">A seguir, há alguns exemplos de como métricas relacionadas à configuração, como as discutidas anteriormente, podem justificar o aumento de investimento na disciplina de Aceleração de implantação.</span><span class="sxs-lookup"><span data-stu-id="46ae7-136">The following are a few examples of how configuration-related metrics, such as those discussed above, can justify an increased investment in the Deployment Acceleration discipline.</span></span>

- <span data-ttu-id="46ae7-137">**Gatilho do contrato de nível de serviço (SLA)**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-137">**Service-level agreement (SLA) trigger**.</span></span> <span data-ttu-id="46ae7-138">Uma empresa que não pode atender seus SLAs para seus clientes externos ou parceiros internos, deve investir na disciplina de Aceleração de implantação para reduzir o tempo de inatividade do sistema.</span><span class="sxs-lookup"><span data-stu-id="46ae7-138">A company that cannot meet its SLAs to its external customers or internal partners should invest in the Deployment Acceleration discipline to reduce system downtime.</span></span>
- <span data-ttu-id="46ae7-139">**Gatilhos de tempo de recuperação**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-139">**Recovery time triggers**.</span></span> <span data-ttu-id="46ae7-140">Se uma empresa exceder os limites necessários para o tempo de recuperação após uma falha do sistema, ela investir em aperfeiçoar sua disciplina de aceleração de implantação e no design do sistema para reduzir ou eliminar falhas ou o efeito do tempo de inatividade do componente individual.</span><span class="sxs-lookup"><span data-stu-id="46ae7-140">If a company exceeds the required thresholds for recovery time following a system failure, it should invest in improving its Deployment Acceleration discipline and systems design to reduce or eliminate failures or the effect of individual component downtime.</span></span>
- <span data-ttu-id="46ae7-141">**Gatilhos de descompasso de configuração**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-141">**Configuration drift triggers**.</span></span> <span data-ttu-id="46ae7-142">Uma empresa que está apresentando mudanças inesperadas na configuração dos componentes do sistema principal ou falhas na implantação ou atualizações de seus sistemas, deverá investir na disciplina de Aceleração de implantação para identificar a causa raiz e as etapas de correção.</span><span class="sxs-lookup"><span data-stu-id="46ae7-142">A company that is experiencing unexpected changes in the configuration of key system components, or failures in the deployment of or updates to its systems, should invest in the Deployment Acceleration discipline to identify root causes and steps for remediation.</span></span>  
- <span data-ttu-id="46ae7-143">**Gatilhos fora de conformidade**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-143">**Out of compliance triggers**.</span></span> <span data-ttu-id="46ae7-144">Se o número de recursos fora de conformidade exceder um limite definido (seja como um número total de recursos ou uma porcentagem do total de recursos), uma empresa deve investir em melhorias na disciplina de Aceleração de implantação para garantir que cada configuração de recurso permaneça em conformidade em todo o ciclo de vida desse recurso.</span><span class="sxs-lookup"><span data-stu-id="46ae7-144">If the number of out-of-compliance resources exceeds a defined threshold (either as a total number of resources or a percentage of total resources), a company should invest in Deployment Acceleration discipline improvements to ensure each resource's configuration remains in compliance throughout that resource's lifecycle.</span></span>
- <span data-ttu-id="46ae7-145">**Gatilhos de agendamento de projeto**.</span><span class="sxs-lookup"><span data-stu-id="46ae7-145">**Project schedule triggers**.</span></span> <span data-ttu-id="46ae7-146">Se o tempo de implantação de aplicativos e recursos da empresa geralmente exceder um limite de definição, a empresa deve investir em seus processos de implantação de aceleração para introduzir ou aprimorar implantações automatizadas para consistência e previsibilidade.</span><span class="sxs-lookup"><span data-stu-id="46ae7-146">If the time to deploy a company's resources and applications often exceed a define threshold, a company should invest in its Deployment Acceleration processes to introduce or improve automated deployments for consistency and predictability.</span></span> <span data-ttu-id="46ae7-147">Tempos de implantação, medidos em dias ou até mesmo semanas geralmente indicam uma estratégia de implantação de aceleração abaixo do ideal.</span><span class="sxs-lookup"><span data-stu-id="46ae7-147">Deployment times measured in days or even weeks usually indicate a suboptimal Deployment Acceleration strategy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="46ae7-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="46ae7-148">Next steps</span></span>

<span data-ttu-id="46ae7-149">Usar o [modelo de Gerenciamento de Nuvem](./template.md), de métricas do documento e de indicadores de tolerância que se alinham ao atual plano de adoção da nuvem.</span><span class="sxs-lookup"><span data-stu-id="46ae7-149">Using the [Cloud Management template](./template.md), document metrics and tolerance indicators that align to the current cloud adoption plan.</span></span>

<span data-ttu-id="46ae7-150">Compilar riscos e tolerância, estabelecer um processo para administrar e comunicar a aderência da política de aceleração de implantação.</span><span class="sxs-lookup"><span data-stu-id="46ae7-150">Building on risks and tolerance, establish a process for governing and communicating Deployment Acceleration policy adherence.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46ae7-151">Estabelecer os processos de conformidade com as políticas</span><span class="sxs-lookup"><span data-stu-id="46ae7-151">Establish policy adherence processes</span></span>](compliance-processes.md)