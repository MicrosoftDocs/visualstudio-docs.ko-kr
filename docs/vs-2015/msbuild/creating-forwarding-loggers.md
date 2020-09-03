---
title: 전달 로거 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ecc9bae7176c0d8c0f79452baff87a7a697db459
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184025"
---
# <a name="creating-forwarding-loggers"></a>전달 로거 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

전달 로거는 다중 프로세서 시스템에서 프로젝트를 빌드할 때 모니터링하려는 이벤트를 선택할 수 있도록 하여 로깅 효율성을 개선합니다. 전달 로거를 사용하여 원하지 않는 이벤트가 중앙 로거를 가득 채우고, 빌드 시간이 느려지고, 로그를 어지럽히지 않도록 방지할 수 있습니다.  
  
 전달 로거를 만들려면 <xref:Microsoft.Build.Framework.IForwardingLogger> 인터페이스를 구현한 다음 해당 메서드를 수동으로 구현하거나, <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 클래스 및 미리 구성된 해당 메서드를 사용할 수 있습니다. (두 번째 방법은 대부분의 애플리케이션에서 충분히 사용할 수 있습니다.)  
  
## <a name="register-events-and-respond-to-them"></a>등록 이벤트 및 해당 이벤트에 대한 응답  
 전달 로거는 보조 빌드 엔진에서 빌드 이벤트를 보고할 때 이에 대한 정보를 수집합니다. 이 작업은 다중 프로세서 시스템에서 빌드하는 동안 기본 빌드 프로세스에 의해 만들어진 작업자 프로세스입니다. 그런 다음 전달 로거는 지정한 지침에 따라 중앙 로거에 전달할 이벤트를 선택합니다.  
  
 전달 로거를 등록하여 모니터링하려는 이벤트를 처리해야 합니다. 이벤트에 등록하려면 로거거 <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> 메서드를 재정의해야 합니다. 이 메서드에는 시스템의 프로세서 수로 설정할 수 있는 `nodecount` 선택적 매개 변수가 포함됩니다. (기본적으로 값은 1입니다.)  
  
 모니터링할 수 있는 이벤트의 예는 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 및 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>입니다.  
  
 다중 프로세서 환경에서 이벤트 메시지는 순서 없이 수신될 가능성이 높습니다. 따라서 전달 로거에서 이벤트 처리기를 사용하여 이벤트를 계산하고 중앙 로거에 전달하기 위해 리디렉터에 전달되는 이벤트를 확인하도록 프로그래밍해야 합니다. 이를 위해 모든 메시지에 연결된 <xref:Microsoft.Build.Framework.BuildEventContext> 클래스를 사용하여 전달하려는 이벤트를 식별한 다음 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 클래스(또는 그 하위 클래스)에 이벤트의 이름을 전달할 수 있습니다. 이 방법을 사용하면 다른 특정 코딩이 이벤트를 전달해야 합니다.  
  
## <a name="specify-a-forwarding-logger"></a>전달 로거 지정  
 전달 로거를 어셈블리로 컴파일한 후에 빌드하는 동안 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서 사용하도록 지시해야 합니다. 이를 위해 MSBuild.exe와 함께 `/FileLogger`, `/FileLoggerParameters` 및 `/DistributedFileLogger` 스위치를 사용합니다. `/FileLogger` 스위치는 MSBuild.exe에서 로거를 직접 연결하도록 지시합니다. `/DistributedFileLogger` 스위치는 노드당 로그 파일이 있음을 의미합니다. 전달 로거에 매개 변수를 설정하려면 `/FileLoggerParameters` 스위치를 사용합니다. 이러한 MSBuild.exe 스위치와 기타 스위치에 대 한 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조 하세요.  
  
## <a name="multi-processor-aware-loggers"></a>다중 프로세서 인식 로거  
 다중 프로세서 시스템에서 프로젝트를 빌드할 때 각 프로세서의 빌드 메시지가 통합 시퀀스에서 자동으로 인터리브되지 않습니다. 대신 모든 메시지에 연결된 <xref:Microsoft.Build.Framework.BuildEventContext> 클래스를 사용하여 메시지 그룹화 우선 순위를 설정해야 합니다. 다중 프로세서 빌드에 대 한 자세한 내용은 [다중 프로세서 환경에서의 로깅](../msbuild/logging-in-a-multi-processor-environment.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [빌드로 거](../msbuild/build-loggers.md)   
 [다중 프로세서 환경에서의 로깅](../msbuild/logging-in-a-multi-processor-environment.md)
