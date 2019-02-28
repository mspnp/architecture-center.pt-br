---
title: 'CAF: Aperfeiçoamento da disciplina de Gerenciamento de Custos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
description: Aperfeiçoamento da disciplina de Gerenciamento de Custos
author: BrianBlanchard
ms.openlocfilehash: 34975d195a95b1a85ada96efe8c76a6138385ec1
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55900410"
---
# <a name="cost-management-discipline-improvement"></a><span data-ttu-id="a9c06-103">Aperfeiçoamento da disciplina de Gerenciamento de Custos</span><span class="sxs-lookup"><span data-stu-id="a9c06-103">Cost Management discipline improvement</span></span>

<span data-ttu-id="a9c06-104">A disciplina de gerenciamento de custos tenta abordar riscos comerciais principais relacionados a despesas incorridas ao hospedar cargas de trabalho baseadas em nuvem.</span><span class="sxs-lookup"><span data-stu-id="a9c06-104">The Cost Management discipline attempts to address core business risks related to expenses incurred when hosting cloud-based workloads.</span></span> <span data-ttu-id="a9c06-105">Dentro de cinco disciplinas de Governança de nuvem, o Gerenciamento de Custos está envolvido no controle de custo e uso de recursos de nuvem com o objetivo de criar e manter um ciclo de custo planejado.</span><span class="sxs-lookup"><span data-stu-id="a9c06-105">Within the five disciplines of Cloud Governance, Cost Management is involved in controlling cost and usage of cloud resources with the goal of creating and maintaining a planned cost cycle.</span></span>

<span data-ttu-id="a9c06-106">Este artigo descreve as tarefas potenciais da sua empresa para realizar para desenvolver e maturar sua disciplina de Gerenciamento de Custos.</span><span class="sxs-lookup"><span data-stu-id="a9c06-106">This article outlines potential tasks your company perform to develop and mature your Cost Management discipline.</span></span> <span data-ttu-id="a9c06-107">Essas tarefas podem ser divididas entre as fases de planejamento, criação, adoção e operacional para a implementação de uma solução de nuvem, que depois são iteradas para permitir o desenvolvimento de uma [abordagem incremental para a governança de nuvem](../journeys/overview.md#an-incremental-approach-to-cloud-governance).</span><span class="sxs-lookup"><span data-stu-id="a9c06-107">These tasks can be broken down into planning, building, adopting, and operating phases of implementing a cloud solution, which are then iterated on allowing the development of an [incremental approach to cloud governance](../journeys/overview.md#an-incremental-approach-to-cloud-governance).</span></span>

![Quatro fases de adoção](../../_images/adoption-phases.png)

<span data-ttu-id="a9c06-109">*Figura 1. Fases de adoção da abordagem incremental da governança de nuvem.*</span><span class="sxs-lookup"><span data-stu-id="a9c06-109">*Figure 1. Adoption phases of the incremental approach to cloud governance.*</span></span>

<span data-ttu-id="a9c06-110">Nenhum documento individual pode contabilizar os requisitos de todas as empresas.</span><span class="sxs-lookup"><span data-stu-id="a9c06-110">No single document can account for the requirements of all businesses.</span></span> <span data-ttu-id="a9c06-111">Portanto, este artigo descreve as atividades de exemplo potenciais e mínimas sugeridas para cada fase do processo de amadurecimento da governança.</span><span class="sxs-lookup"><span data-stu-id="a9c06-111">As such, this article outlines suggested minimum and potential example activities for each phase of the governance maturation process.</span></span> <span data-ttu-id="a9c06-112">O objetivo inicial dessas atividades é ajudar a criar um [MVP de política](../journeys/overview.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para a evolução da política incremental.</span><span class="sxs-lookup"><span data-stu-id="a9c06-112">The initial objective of these activities is to help you build a [Policy MVP](../journeys/overview.md#an-incremental-approach-to-cloud-governance) and establish a framework for incremental policy evolution.</span></span> <span data-ttu-id="a9c06-113">Sua equipe de governança de nuvem precisará decidir o quanto investir nessas atividades para melhorar as funcionalidades de governança de Gerenciamento de Custos.</span><span class="sxs-lookup"><span data-stu-id="a9c06-113">Your Cloud Governance team will need to decide how much to invest in these activities to improve your Cost Management governance capabilities.</span></span>

> [!CAUTION]
> <span data-ttu-id="a9c06-114">Nenhuma das atividades mínimas ou potenciais descritas neste artigo está alinhada a políticas corporativas específicas ou a requisitos de conformidade a terceiros.</span><span class="sxs-lookup"><span data-stu-id="a9c06-114">Neither the minimum or potential activities outlined in this article are aligned to specific corporate policies or third party compliance requirements.</span></span> <span data-ttu-id="a9c06-115">Essas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento de ambos os requisitos com um modelo de governança de nuvem.</span><span class="sxs-lookup"><span data-stu-id="a9c06-115">This guidance is designed to help facilitate the conversations that will lead to alignment of both requirements with a cloud governance model.</span></span>

## <a name="planning-and-readiness"></a><span data-ttu-id="a9c06-116">Planejamento e preparação</span><span class="sxs-lookup"><span data-stu-id="a9c06-116">Planning and readiness</span></span>

<span data-ttu-id="a9c06-117">Esta fase de maturidade de governança une os resultados de negócios e as estratégias realizáveis.</span><span class="sxs-lookup"><span data-stu-id="a9c06-117">This phase of governance maturity bridges the divide between business outcomes and actionable strategies.</span></span> <span data-ttu-id="a9c06-118">Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas ao estado digital e começa a planejar o esforço global de migração.</span><span class="sxs-lookup"><span data-stu-id="a9c06-118">During this process, the leadership team defines specific metrics, maps those metrics to the digital estate, and begins planning the overall migration effort.</span></span>

<span data-ttu-id="a9c06-119">**Atividades mínimas sugeridas:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-119">**Minimum suggested activities:**</span></span>

* <span data-ttu-id="a9c06-120">Avaliar suas opções de [cadeia de ferramentas de Gerenciamento de Custos](toolchain.md).</span><span class="sxs-lookup"><span data-stu-id="a9c06-120">Evaluate your [Cost Management toolchain](toolchain.md) options.</span></span>
* <span data-ttu-id="a9c06-121">Desenvolver um documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.</span><span class="sxs-lookup"><span data-stu-id="a9c06-121">Develop a draft Architecture Guidelines document and distribute to key stakeholders.</span></span>
* <span data-ttu-id="a9c06-122">Treinar e envolver as pessoas e equipes afetadas pelo desenvolvimento das diretrizes de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="a9c06-122">Educate and involve the people and teams affected by the development of Architecture Guidelines.</span></span>

<span data-ttu-id="a9c06-123">**Atividades potenciais:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-123">**Potential activities:**</span></span>

* <span data-ttu-id="a9c06-124">Garantir em decisões orçamentárias que apoiam a justificativa e negócios para a sua estratégia de nuvem.</span><span class="sxs-lookup"><span data-stu-id="a9c06-124">Ensure budgetary decisions that support the business justification for your cloud strategy.</span></span>
* <span data-ttu-id="a9c06-125">Validar as métricas de aprendizado que podem ser usadas para relatar a alocação bem-sucedida de financiamento.</span><span class="sxs-lookup"><span data-stu-id="a9c06-125">Validate learning metrics that you use to report on the successful allocation of funding.</span></span>
* <span data-ttu-id="a9c06-126">Entender o modelo de contabilidade de nuvem desejado que afeta como os custos de nuvem devem ser considerados.</span><span class="sxs-lookup"><span data-stu-id="a9c06-126">Understand the desired cloud accounting model that affects how cloud costs should be accounted for.</span></span>
* <span data-ttu-id="a9c06-127">Familiarizar-se com o plano de imóveis digital e validar as expectativas de custos precisas.</span><span class="sxs-lookup"><span data-stu-id="a9c06-127">Become familiar with the digital estate plan and validate accurate costing expectations.</span></span>
* <span data-ttu-id="a9c06-128">Avaliar as opções de compras para determinar se é melhor "pagar conforme o uso" ou fazer um pré-compromisso com a compra de um Contrato Enterprise.</span><span class="sxs-lookup"><span data-stu-id="a9c06-128">Evaluate buying options to determine if it's better to "pay as you go" or to make a precommitment by purchasing an Enterprise Agreement.</span></span>
* <span data-ttu-id="a9c06-129">Alinhar os objetivos de negócios aos orçamentos planejados e ajuste os planos orçamentários conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a9c06-129">Align business goals with planned budgets and adjust budgetary plans as necessary.</span></span>
* <span data-ttu-id="a9c06-130">Desenvolver metas e orçamento de mecanismo de relatórios para notificar técnicos e stakeholders do negócio no final de cada ciclo de custo.</span><span class="sxs-lookup"><span data-stu-id="a9c06-130">Develop a goals and budget reporting mechanism to notify technical and business stakeholders at the end of each cost cycle.</span></span>

## <a name="build-and-pre-deployment"></a><span data-ttu-id="a9c06-131">Compilação e pré-implantação</span><span class="sxs-lookup"><span data-stu-id="a9c06-131">Build and pre-deployment</span></span>

<span data-ttu-id="a9c06-132">Diversos pré-requisitos técnicos e não técnicos são necessários para migrar um ambiente com sucesso.</span><span class="sxs-lookup"><span data-stu-id="a9c06-132">A number of technical and nontechnical prerequisites are required to successfully migrate an environment.</span></span> <span data-ttu-id="a9c06-133">Esse processo se concentra nas decisões, na preparação e na infraestrutura central que ocorrem após uma migração.</span><span class="sxs-lookup"><span data-stu-id="a9c06-133">This process focuses on the decisions, readiness, and core infrastructure that proceeds a migration.</span></span>

<span data-ttu-id="a9c06-134">**Atividades mínimas sugeridas:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-134">**Minimum suggested activities:**</span></span>

* <span data-ttu-id="a9c06-135">Implementar sua [cadeia de ferramentas de Gerenciamento de Custos](toolchain.md), lançando em uma fase de pré-implantação.</span><span class="sxs-lookup"><span data-stu-id="a9c06-135">Implement your [Cost Management toolchain](toolchain.md) by rolling out in a pre-deployment phase.</span></span>
* <span data-ttu-id="a9c06-136">Atualizar o documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.</span><span class="sxs-lookup"><span data-stu-id="a9c06-136">Update the Architecture Guidelines document and distribute to key stakeholders.</span></span>
* <span data-ttu-id="a9c06-137">Desenvolver materiais e documentações educativas, comunicações de conscientização, incentivos e outros programas para ajudar a conduzir a adoção de usuários.</span><span class="sxs-lookup"><span data-stu-id="a9c06-137">Develop educational materials and documentation, awareness communications, incentives, and other programs to help drive user adoption.</span></span>
* <span data-ttu-id="a9c06-138">Determine se seus requisitos de compra se alinham às suas metas e orçamentos.</span><span class="sxs-lookup"><span data-stu-id="a9c06-138">Determine if your purchase requirements align with your budgets and goals.</span></span>

<span data-ttu-id="a9c06-139">**Atividades potenciais:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-139">**Potential activities:**</span></span>

* <span data-ttu-id="a9c06-140">Alinhar seus planos de orçamento à [Estratégia de assinatura](../../decision-guides/subscriptions/overview.md) que define o modelo de propriedade de núcleo.</span><span class="sxs-lookup"><span data-stu-id="a9c06-140">Align your budgetary plans with the [Subscription Strategy](../../decision-guides/subscriptions/overview.md) that defines your core ownership model.</span></span>
* <span data-ttu-id="a9c06-141">Usar a [Estratégia de Consistência de Recursos](../../decision-guides/resource-consistency/overview.md) para impor diretrizes de arquitetura ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="a9c06-141">Leverage the [Resource Consistency Strategy](../../decision-guides/resource-consistency/overview.md) to enforce architecture and cost guidelines over time.</span></span>
* <span data-ttu-id="a9c06-142">Determinar se há quaisquer anomalias de custo que afetem seus planos de migração e adoção.</span><span class="sxs-lookup"><span data-stu-id="a9c06-142">Determine if there are any cost anomalies that affect your adoption and migration plans.</span></span>

## <a name="adopt-and-migrate"></a><span data-ttu-id="a9c06-143">Adotar e migrar</span><span class="sxs-lookup"><span data-stu-id="a9c06-143">Adopt and migrate</span></span>

<span data-ttu-id="a9c06-144">A migração é um processo incremental que se concentra no movimento, teste e adoção de aplicativos ou cargas de trabalho em um estado digital existente.</span><span class="sxs-lookup"><span data-stu-id="a9c06-144">Migration is an incremental process that focuses on the movement, testing, and adoption of applications or workloads in an existing digital estate.</span></span>

<span data-ttu-id="a9c06-145">**Atividades mínimas sugeridas:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-145">**Minimum suggested activities:**</span></span>

* <span data-ttu-id="a9c06-146">Migrar sua [cadeia de ferramentas de Gerenciamento de Custos](toolchain.md) da pré-implantação para produção.</span><span class="sxs-lookup"><span data-stu-id="a9c06-146">Migrate your [Cost Management toolchain](toolchain.md) from pre-deployment to production.</span></span>
* <span data-ttu-id="a9c06-147">Atualizar o documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.</span><span class="sxs-lookup"><span data-stu-id="a9c06-147">Update the Architecture Guidelines document and distribute to key stakeholders.</span></span>
* <span data-ttu-id="a9c06-148">Desenvolver materiais e documentações educativas, comunicações de conscientização, incentivos e outros programas para ajudar a conduzir a adoção de usuários.</span><span class="sxs-lookup"><span data-stu-id="a9c06-148">Develop educational materials and documentation, awareness communications, incentives, and other programs to help drive user adoption.</span></span>

<span data-ttu-id="a9c06-149">**Atividades potenciais:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-149">**Potential activities:**</span></span>

* <span data-ttu-id="a9c06-150">Implemente seu modelo de Contabilidade de Nuvem.</span><span class="sxs-lookup"><span data-stu-id="a9c06-150">Implement your Cloud Accounting Model.</span></span>
* <span data-ttu-id="a9c06-151">Certifique-se de que seus orçamentos refletem seus gastos reais durante cada versão e ajuste conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a9c06-151">Ensure that your budgets reflect your actual spending during each release and adjust as necessary.</span></span>
* <span data-ttu-id="a9c06-152">Monitore as alterações nos planos de acesso a recursos e valide com os stakeholders se forem necessárias aprovações adicionais.</span><span class="sxs-lookup"><span data-stu-id="a9c06-152">Monitor changes in budgetary plans and validate with stakeholders if additional sign-offs are needed.</span></span>
* <span data-ttu-id="a9c06-153">Atualizar as alterações no documento de Diretrizes de arquitetura para refletir os custos reais.</span><span class="sxs-lookup"><span data-stu-id="a9c06-153">Update changes to the Architecture Guidelines document to reflect actual costs.</span></span>

## <a name="operate-and-post-implementation"></a><span data-ttu-id="a9c06-154">Operação e pós-implementação</span><span class="sxs-lookup"><span data-stu-id="a9c06-154">Operate and post-implementation</span></span>

<span data-ttu-id="a9c06-155">Depois que a transformação for concluída, a governança e as operações devem ser mantidas para o ciclo de vida natural de um aplicativo ou uma carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a9c06-155">Once the transformation is complete, governance and operations must live on for the natural lifecycle of an application or workload.</span></span> <span data-ttu-id="a9c06-156">Essa fase de maturidade de governança se concentra em atividades que normalmente ocorrem depois que a solução é implementada e que o ciclo de transformação começa a se estabilizar.</span><span class="sxs-lookup"><span data-stu-id="a9c06-156">This phase of governance maturity focuses on the activities that commonly come after the solution is implemented and the transformation cycle begins to stabilize.</span></span>

<span data-ttu-id="a9c06-157">**Atividades mínimas sugeridas:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-157">**Minimum suggested activities:**</span></span>

* <span data-ttu-id="a9c06-158">Personalizar sua [cadeia de ferramentas de Gerenciamento de Custos](toolchain.md) baseada em alterações nas necessidades de gerenciamento de custo da sua organização.</span><span class="sxs-lookup"><span data-stu-id="a9c06-158">Customize your [Cost Management toolchain](toolchain.md) based on changes in your organization’s cost management needs.</span></span>
* <span data-ttu-id="a9c06-159">Cogitar automatizar quaisquer notificações e relatórios para refletir o gasto real.</span><span class="sxs-lookup"><span data-stu-id="a9c06-159">Consider automating any notifications and reports to reflect actual spending.</span></span>
* <span data-ttu-id="a9c06-160">Refinar as Diretrizes de arquitetura para orientar processos futuros de adoção.</span><span class="sxs-lookup"><span data-stu-id="a9c06-160">Refine Architecture Guidelines to guide future adoption processes.</span></span>
* <span data-ttu-id="a9c06-161">Treinar as equipes afetadas periodicamente para garantir a conformidade contínua às Diretrizes de Arquitetura.</span><span class="sxs-lookup"><span data-stu-id="a9c06-161">Educate affected teams on a periodic basis to ensure ongoing adherence to the Architecture Guidelines.</span></span>

<span data-ttu-id="a9c06-162">**Atividades potenciais:**</span><span class="sxs-lookup"><span data-stu-id="a9c06-162">**Potential activities:**</span></span>

* <span data-ttu-id="a9c06-163">Executar uma análise de negócios trimestral de nuvem para comunicar o valor fornecido para os negócios e os custos associados.</span><span class="sxs-lookup"><span data-stu-id="a9c06-163">Execute a quarterly cloud business review to communicate value delivered to the business and associated costs.</span></span>
* <span data-ttu-id="a9c06-164">Ajustar planos trimestrais para refletir as alterações aos gastos reais.</span><span class="sxs-lookup"><span data-stu-id="a9c06-164">Adjust plans quarterly to reflect changes to actual spending.</span></span>
* <span data-ttu-id="a9c06-165">Determinar o alinhamento financeiro para perdas e ganhos para assinaturas de unidade de negócios.</span><span class="sxs-lookup"><span data-stu-id="a9c06-165">Determine financial alignment to P&Ls for business unit subscriptions.</span></span>
* <span data-ttu-id="a9c06-166">Analisar o valor do stakeholder e os métodos de relatórios de custo em uma base mensal.</span><span class="sxs-lookup"><span data-stu-id="a9c06-166">Analyze stakeholder value and cost reporting methods on a monthly basis.</span></span>
* <span data-ttu-id="a9c06-167">Avaliar os recursos subutilizados e determine se vale a pena mantê-los.</span><span class="sxs-lookup"><span data-stu-id="a9c06-167">Remediate underused assets and determine if they're worth continuing.</span></span>
* <span data-ttu-id="a9c06-168">Detectar desalinhamentos e anomalias entre os gastos reais e planejados.</span><span class="sxs-lookup"><span data-stu-id="a9c06-168">Detect misalignments and anomalies between the plan and actual spending.</span></span>
* <span data-ttu-id="a9c06-169">Auxiliar as equipes de adoção da nuvem e a equipe de estratégia de nuvem a entender e resolver essas anomalias.</span><span class="sxs-lookup"><span data-stu-id="a9c06-169">Assist the cloud adoption teams and the Cloud Strategy team with understanding and resolving these anomalies.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a9c06-170">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a9c06-170">Next steps</span></span>

<span data-ttu-id="a9c06-171">Agora que você entende o conceito de governança de identidade de nuvem, examine a [cadeia de ferramentas de Gerenciamento de Custos](toolchain.md) para identificar as ferramentas do Azure e recursos que você precisará ao desenvolver a disciplina de governança da de Gerenciamento de Custos na plataforma do Azure.</span><span class="sxs-lookup"><span data-stu-id="a9c06-171">Now that you understand the concept of cloud identity governance, examine the [Cost Management toolchain](toolchain.md) to identify Azure tools and features that you'll need when developing the Cost Management governance discipline on the Azure platform.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a9c06-172">Cadeia de ferramentas de Gerenciamento de Custos do Azure</span><span class="sxs-lookup"><span data-stu-id="a9c06-172">Cost Management toolchain for Azure</span></span>](toolchain.md)