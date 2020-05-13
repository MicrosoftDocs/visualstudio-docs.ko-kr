---
title: 다중 프로세서 환경에서의 로그인 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c332fb67e96bdfea0059de11441da7c32871633
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633566"
---
# <a name="logging-in-a-multi-processor-environment"></a>다중 프로세서 환경에서의 로그인

MSBuild에서는 다중 프로세서를 사용할 수 있기 때문에 프로젝트 빌드 시간을 크게 줄일 수 있는 반면 로깅은 복잡해집니다. 단일 프로세서 환경에서 로거는 예측 가능하고 순차적인 방식으로 들어오는 이벤트, 메시지, 경고 및 오류를 처리할 수 있습니다. 그러나 다중 프로세서 환경에서 여러 원본의 이벤트는 동시에 또는 순서 없이 도착할 수 있습니다. MSBuild에서는 새 다중 프로세서 인식 로거가 제공되며, 사용자 지정 "전달 로거"를 만들 수 있습니다.

## <a name="log-multiple-processor-builds"></a>다중 프로세서 빌드 로깅

다중 프로세서 또는 다중 핵심 프로세서에서 하나 이상의 프로젝트를 빌드하면 모든 프로젝트에 대한 MSBuild 빌드 이벤트가 동시에 생성됩니다. 따라서 많은 이벤트 데이터가 로거에 동시에 또는 순서 없이 도착할 수 있습니다. 그러면 로거에 과부하가 걸리고 빌드 시간이 늘어나거나 로거 출력이 잘못되거나 심지어 빌드가 손상될 수 있습니다. 이러한 문제를 해결하기 위해 MSBuild 로거를 사용하면 순서 없는 이벤트를 처리하고 이벤트와 해당 소스를 서로 연결할 수 있습니다.

사용자 지정 전달 로거를 만들어 로깅 효율성을 더욱 향상시킬 수 있습니다. 사용자 지정 전달 로거는 빌드하기 전에 모니터링하려는 이벤트를 선택하도록 하여 필터의 역할을 합니다. 사용자 지정 전달 로거를 사용하면 원하지 않는 이벤트는 로거에 과부하가 걸리지 않도록 하고, 로그를 복잡하게 하거나 빌드 시간을 느리게 하지 않습니다.

### <a name="central-logging-model"></a>중앙 로깅 모델

다중 프로세서 빌드의 경우 MSBuild는 "중앙 로깅 모델"을 사용합니다. 중앙 로깅 모델에서 *MSBuild.exe*의 인스턴스는 기본 빌드 프로세스 또는 “중앙 노드”의 역할을 합니다. *MSBuild.exe*의 보조 인스턴스 또는 “보조 노드”는 중앙 노드에 연결됩니다. 중앙 노드에 연결된 모든 ILogger 기반 로거는 "중앙 로거"라고 하며 보조 노드에 연결된 로거는 "보조 로거"라고 합니다.

빌드가 발생하면 보조 로거는 중앙 로거로 이벤트 트래픽을 라우팅합니다. 이벤트는 여러 개의 보조 노드에서 들어오므로 데이터는 중앙 노드에 동시에 도착하지만 인터리브됩니다. 이벤트-프로젝트 및 이벤트-대상 참조를 해결하기 위해 이벤트 인수는 추가 빌드 이벤트 컨텍스트 정보를 포함합니다.

<xref:Microsoft.Build.Framework.ILogger>는 중앙 로거에 의해 구현되어야 하지만 중앙 로거에서 빌드에 참여하는 노드 수로 초기화하려는 경우 <xref:Microsoft.Build.Framework.INodeLogger>도 구현하는 것이 좋습니다. 다음 <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 메서드의 오버로드는 엔진이 로거를 초기화할 때 호출됩니다.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>분산 로깅 모델

중앙 로깅 모델에서 여러 프로젝트를 한 번에 빌드하는 경우와 같이 너무 많이 들어오는 메시지 트래픽은 중앙 노드에 과부하가 걸리도록 할 수 있습니다. 이는 시스템에 과부하를 주고 빌드 성능을 낮춥니다.

이 문제를 줄이기 위해 MSBuild는 전달 로거를 만들도록 하여 중앙 로깅 모델을 확장하는 "분산된 로깅 모델"을 활성화합니다. 전달 로거는 보조 노드에 연결되며 해당 노드에서 들어오는 빌드 이벤트를 받습니다. 전달 로거는 이벤트를 필터링한 다음 중앙 노드에 원하는 이벤트만 전달할 수 있는 것을 제외하고 일반 로거와 동일합니다. 이는 중앙 노드에서 메시지 트래픽을 감소시키므로 더 나은 성능을 활성화합니다.

 <xref:Microsoft.Build.Framework.IForwardingLogger>에서 파생된 <xref:Microsoft.Build.Framework.ILogger> 인터페이스를 구현하여 전달 로거를 만들 수 있습니다. 인터페이스는 다음과 같이 정의됩니다.

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

전달 로거에서 이벤트를 전달하려면 <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> 인터페이스의 <xref:Microsoft.Build.Framework.IEventRedirector> 메서드를 호출합니다. 매개 변수로 적절한 <xref:Microsoft.Build.Framework.BuildEventArgs> 또는 파생 개체를 전달합니다.

자세한 내용은 [전달 로거 만들기](../msbuild/creating-forwarding-loggers.md)를 참조하세요.

### <a name="attaching-a-distributed-logger"></a>분산된 로거 연결

명령줄 빌드에서 분산된 로거를 연결하려면 `-distributedlogger`(또는 간단히 `-dl`) 스위치를 사용합니다. 로거 형식 및 클래스의 이름을 지정하기 위한 형식은 분산된 로거가 두 개의 로깅 클래스(전달 로거 및 중앙 로거)로 구성된 것을 제외하고 `-logger` 스위치에 대한 것과 동일합니다. 다음은 분산된 로거 연결의 예입니다.

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

별표(*)는 `-dl` 스위치에서 두 개의 로거 이름을 구분합니다.

## <a name="see-also"></a>참고 항목

- [빌드 로거](../msbuild/build-loggers.md)
- [전달 로거 만들기](../msbuild/creating-forwarding-loggers.md)
