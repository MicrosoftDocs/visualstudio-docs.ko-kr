---
title: 레거시 워크플로 활동 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fb741afd7488717ba85e68ea7fd982e3e1d5adf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849242"
---
# <a name="legacy-workflow-activities"></a>레거시 워크플로 활동
[!INCLUDE[wf](../includes/wf-md.md)] 에는 제어 흐름, 조건, 이벤트 처리, 상태 관리, 응용 프로그램 및 서비스와의 통신을 위한 기능을 제공 하는 기본 작업 집합이 포함 되어 있습니다. 워크플로를 디자인할 때 [!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 제공한 시스템 제공 활동을 사용하거나 사용자가 직접 사용자 지정 활동을 만들 수 있습니다.

 다음 표에서는 기본적으로 제공되는 [!INCLUDE[wf2](../includes/wf2-md.md)]프레임워크 활동 집합을 보여 줍니다. 이러한 활동의 대부분은의 **도구 상자** 에서 액세스할 수 있는 활동 디자이너로 표현 됩니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] . 활동을 만들려면 **도구 상자** 에서 해당 디자이너를 끌어서 디자인 화면에 놓습니다.

|작업|Description|
|--------------|-----------------|
|[CallExternalMethodActivity](https://msdn2.microsoft.com/library/system.workflow.activities.callexternalmethodactivity.aspx)|로컬 서비스와의 입출력 통신을 위해 **HandleExternalEventActivity** 활동과 함께 사용 됩니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CallExternalMethodActivity 활동 사용](https://msdn2.microsoft.com/library/bb628493.aspx).|
|[CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx)|모든 복합 활동의 자식 활동이 실행을 완료하기 전에 취소된 복합 활동의 정리 논리를 포함시킬 때 사용합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CancellationHandlerActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628604.aspx)합니다.|
|[CodeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.codeactivity.aspx)|워크플로에 Visual Basic 또는 C# 코드를 추가할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CodeActivity 활동을 사용](https://msdn2.microsoft.com/library/bb675249.aspx)합니다.|
|[CompensatableSequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.compensatablesequenceactivity.aspx)|[SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx)의 보정 가능한 버전입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableSequenceActivity 활동을 사용](https://msdn2.microsoft.com/library/bb675224.aspx)합니다.|
|[CompensatableTransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensatabletransactionscopeactivity.aspx)|**TransactionScopeActivity**의 보정 가능한 버전입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableTransactionScopeActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628592.aspx)합니다.|
|[CompensateActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensateactivity.aspx)|오류가 발생하면 워크플로에서 이미 수행한 작업을 실행 취소하거나 보정하기 위해 코드를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensateActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628608.aspx)합니다.|
|[CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx)|[!INCLUDE[crdefault](../includes/crdefault-md.md)] [CompensationHandlerActivity 활동을 사용 하 여](https://msdn2.microsoft.com/library/bb675279.aspx)완료 된 TransactionScopeActivity 활동에 대 한 보정을 수행 하는 하나 이상의 활동에 대 한 래퍼입니다.|
|[ConditionedActivityGroup 클래스](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)|[ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) 활동 자체에 적용 되는 조건과 각 자식에 별도로 적용 되는 조건에 따라 자식 활동을 실행 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ConditionedActivityGroup 활동을 사용](https://msdn2.microsoft.com/library/bb675237.aspx)합니다.|
|[DelayActivity](https://msdn2.microsoft.com/library/system.workflow.activities.delayactivity.aspx)|시간 제한 간격을 기반으로 한 지연을 워크플로에 빌드할 수 있습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][DelayActivity 활동 사용](https://msdn2.microsoft.com/library/bb628484.aspx).|
|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)|지정된 이벤트가 발생할 때 실행되는 활동을 하나 이상 래핑합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventDrivenActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628466.aspx)합니다.|
|[EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx)|이벤트와 활동을 연결하는 프레임워크를 제공합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlersActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628537.aspx)합니다.|
|[EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)|[EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx)를 사용 하 여 주 자식 활동을 동시에 실행 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlingScopeActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628463.aspx)합니다.|
|[FaultHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandleractivity.aspx)|지정하는 형식의 예외를 처리하는 데 사용합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlerActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628479.aspx)합니다.|
|[FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx)|[FaultHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandleractivity.aspx)형식의 자식 활동을 순서 대로 나열 하는 복합 활동을 나타냅니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlersActivity 활동을 사용](https://msdn2.microsoft.com/library/bb675252.aspx)합니다.|
|[HandleExternalEventActivity](https://msdn2.microsoft.com/library/system.workflow.activities.handleexternaleventactivity.aspx)|로컬 서비스와의 입출력 통신을 위해 [Callexternalmethodactivity](https://msdn2.microsoft.com/library/system.workflow.activities.callexternalmethodactivity.aspx) 활동과 함께 사용 됩니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][HandleExternalEventActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628446.aspx)합니다.|
|[IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx)|각 분기에서 조건을 테스트 하 고 조건이 **true**인 첫 번째 분기에서 활동을 수행 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][IfElseActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628472.aspx)합니다.|
|[IfElseBranchActivity (영문 페이지일 수 있음)](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)|[IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx)의 분기를 나타냅니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][IfElseBranchActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628465.aspx)합니다.|
|[InvokeWebServiceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.invokewebserviceactivity.aspx)|워크플로에서 웹 서비스를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWebServiceActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628576.aspx)합니다.|
|[InvokeWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.invokeworkflowactivity.aspx)|워크플로에서 다른 워크플로를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWorkflowActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628557.aspx)합니다.|
|[ListenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.listenactivity.aspx)|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx) 자식 활동만 포함 하는 복합 활동입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ListenActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628468.aspx)합니다.|
|[ParallelActivity](https://msdn2.microsoft.com/library/system.workflow.activities.parallelactivity.aspx)|동시에 처리 하기 위해 두 개 이상의 자식 **SequenceActivity** 활동 분기를 예약 하는 방법을 제공 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ParallelActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628494.aspx)합니다.|
|[PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)|규칙 컬렉션을 나타낼 때 사용합니다. 규칙은 조건과 그 결과 작업으로 구성됩니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Policyactivity 활동 사용](https://msdn2.microsoft.com/library/bb675229.aspx).|
|[ReplicatorActivity (영문 페이지일 수 있음)](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)|단일 자식 활동의 여러 인스턴스를 만듭니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ReplicatorActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628544.aspx)합니다.|
|[SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx)|순차 실행을 위해 여러 활동을 함께 연결하는 간단한 방법을 제공합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SequenceActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628551.aspx)합니다.|
|[SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx)|새 상태로의 전환을 지정합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SetStateActivity 활동 사용](https://msdn2.microsoft.com/library/bb628469.aspx).|
|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx)|상태 시스템 워크플로의 상태를 나타냅니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateActivity 활동 사용](https://msdn2.microsoft.com/library/bb628612.aspx).|
|[StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)|**Stateactivity** 활동을 나갈 때 실행 되는 자식 활동의 컨테이너로 [stateactivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) 활동에서 사용 됩니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateFinalizationActivity 활동을 사용](https://msdn2.microsoft.com/library/bb675278.aspx)합니다.|
|[StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)|Stateactivity 활동 [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) 에서 **stateactivity** 활동을 입력할 때 실행 되는 자식 활동의 컨테이너로 사용 됩니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateInitializationActivity 활동을 사용](https://msdn2.microsoft.com/library/bb675253.aspx)합니다.|
|[SuspendActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.suspendactivity.aspx)|특별한 주의가 필요한 일부 오류 조건이 발생할 경우 개입할 수 있도록 워크플로 작업을 일시 중단합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SuspendActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628533.aspx)합니다.|
|[SynchronizationScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.synchronizationscopeactivity.aspx)|동기화된 도메인에서 포함된 활동을 순차적으로 실행합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SynchronizationScopeActivity 활동을 사용](https://msdn2.microsoft.com/library/bb675276.aspx)합니다.|
|[TerminateActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.terminateactivity.aspx)|오류 조건이 발생할 경우 즉시 워크플로 작업을 중지할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][TerminateActivity 활동을 사용](https://msdn2.microsoft.com/library/bb675261.aspx)합니다.|
|[ThrowActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.throwactivity.aspx)|워크플로에 대해 프로세스 메타데이터의 일부로 throw된 비즈니스 예외를 캡처할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ThrowActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628490.aspx)합니다.|
|[TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)|트랜잭션 및 예외 처리를 위한 프레임워크를 제공합니다. 자세한 내용은 [TransactionScopeActivity 활동 사용](https://msdn2.microsoft.com/library/bb675241.aspx)을 참조 하세요.|
|[WebServiceFaultActivity](https://msdn2.microsoft.com/library/system.workflow.activities.webservicefaultactivity.aspx)|웹 서비스 오류 발생을 모델링할 수 있습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceFaultActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628568.aspx)합니다.|
|[WebServiceInputActivity](https://msdn2.microsoft.com/library/system.workflow.activities.webserviceinputactivity.aspx)|웹 서비스에서 데이터를 받습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceInputActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628508.aspx)합니다.|
|[WebServiceOutputActivity](https://msdn2.microsoft.com/library/system.workflow.activities.webserviceoutputactivity.aspx)|워크플로에 대한 웹 서비스 요청에 응답합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceOutputActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628594.aspx)합니다.|
|[WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)|조건이 충족될 때까지 워크플로가 반복될 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WhileActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628552.aspx)합니다.|

 [!INCLUDE[crabout](../includes/crabout-md.md)] 사용자 지정 작업을 만드는 방법 [사용자 지정 작업 개발](https://msdn2.microsoft.com/library/bb675248.aspx) 및 [레거시 Activity Designer 사용](../workflow-designer/using-the-legacy-activity-designer.md)을 참조 하세요.

## <a name="in-this-section"></a>섹션 내용
 [활동 뷰 (레거시)](../workflow-designer/activity-views-legacy.md) 활동의 여러 디자인 뷰에 대해 설명 합니다.

 [방법: 도구 상자에 활동 추가 (레거시)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) 도구 상자에 활동을 추가 하는 방법을 보여 줍니다.

 [방법: 선언적 규칙 조건 만들기 (레거시)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) 선언적 규칙 조건을 만드는 단계를 보여 줍니다.

 [방법: PolicyActivity 규칙 집합 만들기 (레거시)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) PolicyActivity 규칙 집합을 만드는 단계를 보여 줍니다.

 [방법: WCF 계약 작업 구현 (레거시)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 계약 작업을 구현 하는 단계를 보여 줍니다 [!INCLUDE[indigo2](../includes/indigo2-md.md)] .

 [방법: WCF 계약 작업 호출 (레거시)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) 계약 작업을 호출 하는 단계를 보여 줍니다 [!INCLUDE[indigo2](../includes/indigo2-md.md)] .

## <a name="see-also"></a>관련 항목
 [Windows Workflow Foundation 작업](https://msdn2.microsoft.com/library/bb675247.aspx) 워크플로 [개발](https://msdn2.microsoft.com/library/bb628448.aspx) [워크플로 활동 개발](https://msdn2.microsoft.com/library/bb675248.aspx)
