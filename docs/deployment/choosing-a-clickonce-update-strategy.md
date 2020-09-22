---
title: ClickOnce 업데이트 전략 선택 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbddf759841dbe9626868d6c00f42a0849d70520
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841666"
---
# <a name="choose-a-clickonce-update-strategy"></a>ClickOnce 업데이트 전략 선택
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]는 애플리케이션 자동 업데이트를 제공할 수 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션은 배포 매니페스트 파일을 주기적으로 읽어서 애플리케이션의 업데이트가 사용 가능한지 확인합니다. 사용 가능한 경우 새 버전의 애플리케이션을 다운로드하여 실행합니다. 효율성을 위해 변경된 파일만 다운로드합니다.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션을 디자인할 경우 애플리케이션에서 사용 가능한 업데이트를 확인하는 데 사용할 전략을 결정해야 합니다. 사용할 수 있는 세 가지 기본 전략은 애플리케이션 시작 시 업데이트 확인, 애플리케이션 시작 후 업데이트 확인(백그라운드 스레드에서 실행) 또는 업데이트용 사용자 인터페이스 제공입니다.

 또한 애플리케이션에서 업데이트를 확인하는 빈도를 결정하고 업데이트를 필수로 만들 수 있습니다.

> [!NOTE]
> 애플리케이션 업데이트를 사용하려면 네트워크 연결이 필요합니다. 네트워크에 연결되어 있지 않으면 선택한 업데이트 전략에 관계없이 애플리케이션은 업데이트를 확인하지 않고 실행됩니다.

> [!NOTE]
> .NET Framework 2.0 및 .NET Framework 3.0에서는 시작 전이나 후에 사용자 애플리케이션에서 업데이트를 확인하거나 \<xref:System.Deployment.Application> API를 사용하여 배포 매니페스트의 `deploymentProvider`를 설정해야 합니다. `deploymentProvider`요소는 Visual Studio에서 **게시** 탭의 **업데이트** 대화 상자에 있는 **업데이트 위치** 필드에 해당 합니다. 이 규칙은 .NET Framework 3.5에서 완화 됩니다. 자세한 내용은 다시 서명를 사용 [하지 않고 테스트 및 프로덕션 서버용 ClickOnce 응용 프로그램 배포](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)를 참조 하세요.

## <a name="check-for-updates-after-application-startup"></a>응용 프로그램 시작 후 업데이트 확인
 이 전략을 사용하면 애플리케이션에서는 실행 중 백그라운드에서 배포 매니페스트 파일을 찾아 읽으려고 합니다. 사용 가능한 업데이트가 있을 경우 다음 번에 사용자가 애플리케이션을 실행하면 업데이트를 다운로드하여 설치할지 묻는 메시지가 표시됩니다.

 이 전략은 저대역폭 네트워크 연결 또는 다운로드에 시간이 오래 걸릴 수 있는 대규모 애플리케이션에 가장 적합합니다.

 이 업데이트 전략을 사용하려면 **애플리케이션 업데이트** 대화 상자의 **애플리케이션이 업데이트를 확인하는 시기 선택** 섹션에서 **애플리케이션 시작 후**를 클릭합니다. 그런 다음, **애플리케이션이 업데이트를 확인하는 빈도 지정** 섹션에서 업데이트 간격을 지정합니다.

 이 전략은 배포 매니페스트에서 **업데이트** 요소를 다음과 같이 변경하는 것과 같습니다.

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <expiration maximumAge="6" unit="hours" />
   </update>
</subscription>
```

## <a name="check-for-updates-before-application-startup"></a>응용 프로그램 시작 전에 업데이트 확인
 기본 전략은 애플리케이션이 시작되기 전에 배포 매니페스트 파일을 찾아 읽는 것입니다. 이 전략을 사용하면 사용자가 애플리케이션을 시작할 때마다 애플리케이션에서는 배포 매니페스트 파일을 찾아서 읽으려고 합니다. 사용 가능한 업데이트가 있을 경우 업데이트가 다운로드되고, 그렇지 않으면 기존 버전의 애플리케이션이 시작됩니다.

 이 전략은 고대역폭 네트워크 연결에 가장 적합하며, 저대역폭 연결을 통해서는 애플리케이션 시작이 상당히 긴 시간 동안 지연될 수 있습니다.

 이 업데이트 전략을 사용하려면 **애플리케이션 업데이트** 대화 상자의 **애플리케이션이 업데이트를 확인하는 시기 선택** 섹션에서 **애플리케이션 시작 전**을 클릭합니다.

 이 전략은 배포 매니페스트에서 **업데이트** 요소를 다음과 같이 변경하는 것과 같습니다.

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <beforeApplicationStartup />
   </update>
</subscription>
```

## <a name="make-updates-required"></a>업데이트 필요
 사용자가 업데이트된 버전의 애플리케이션을 실행하도록 해야 할 경우가 있습니다. 예를 들어, 이전 버전의 애플리케이션이 올바로 작동하지 않게 하는 웹 서비스 같은 외부 리소스를 변경할 수 있습니다. 이 경우 업데이트를 필수로 표시하여 사용자가 이전 버전을 실행하지 못하도록 합니다.

> [!NOTE]
> 다른 업데이트 전략을 사용하여 업데이트를 요구할 수도 있지만 이전 버전을 실행할 수 없게 하려면 **애플리케이션 시작 전**을 선택해야 합니다. 시작 시 필수 업데이트가 발견되면 사용자는 업데이트를 적용하거나 애플리케이션을 닫아야 합니다.

 업데이트를 필수로 표시하려면 **애플리케이션 업데이트** 대화 상자에서 **이 애플리케이션에 필요한 최소 버전 지정**을 클릭하고 **주 버전**, **부 버전**, **빌드 버전** 및 **수정 버전**으로 구성된 게시 버전을 지정합니다. 이렇게 하면 설치할 수 있는 최하위 버전의 애플리케이션이 지정됩니다.

 이 전략은 배포 매니페스트에서 **배포** 요소의 **minimumRequiredVersion** 특성을 다음과 같이 설정하는 것과 같습니다.

```xml
<deployment install="true" minimumRequiredVersion="1.0.0.0">
```

## <a name="specify-update-intervals"></a>업데이트 간격 지정
 애플리케이션이 업데이트를 확인하는 빈도를 지정할 수도 있습니다. 이렇게 하려면 이 항목의 앞부분에 나오는 &quot;애플리케이션 시작 후 업데이트 확인&quot;에 설명된 대로 애플리케이션 시작 후 업데이트를 확인하도록 지정합니다.

 업데이트 간격을 지정하려면 **애플리케이션 업데이트** 대화 상자에서 **애플리케이션이 업데이트를 확인해야 하는 빈도 지정**을 클릭합니다.

 이 전략은 배포 매니페스트에서 **업데이트** 요소의 **maximumAge** 및 **unit** 특성을 설정하는 것과 같습니다.

 예를 들어, 애플리케이션을 실행할 때마다 확인하거나 일주일에 한 번 또는 한 달에 한 번 확인하려고 할 수 있습니다. 네트워크가 지정한 시간에 연결되어 있지 않으면 다음 번에 애플리케이션을 실행하면 업데이트 확인이 수행됩니다.

## <a name="provide-a-user-interface-for-updates"></a>업데이트에 대 한 사용자 인터페이스 제공
 이 전략을 사용하면 애플리케이션 개발자가 사용자가 애플리케이션에서 업데이트를 확인할 시간 및 빈도를 선택하는 데 사용할 수 있는 사용자 인터페이스를 제공합니다. 예를 들어, "지금 업데이트 확인" 명령 또는 다양한 업데이트 간격을 선택할 수 있는 "업데이트 설정" 대화 상자를 제공할 수 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포 API는 고유한 업데이트 사용자 인터페이스를 프로그래밍할 수 있는 프레임워크를 제공합니다. 자세한 내용은 <xref:System.Deployment.Application> 네임스페이스를 참조하세요.

 애플리케이션이 배포 API를 사용하여 고유 업데이트 논리를 제어하는 경우 다음 단원에 나오는 &quot;업데이트 확인 차단&quot;에서 설명하는 것처럼 업데이트 확인을 차단해야 합니다.

 이 전략은 여러 사용자에 대해 서로 다른 업데이트 전략이 필요한 경우 가장 적합합니다.

## <a name="block-update-checking"></a>업데이트 확인 차단
 애플리케이션에서 업데이트를 확인하지 않도록 할 수도 있습니다. 예를 들어, 업데이트되지 않는 간단한 애플리케이션이 있을 수 있지만 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포를 사용하여 쉽게 설치하려고 합니다.

 응용 프로그램에서 배포 Api를 사용 하 여 자체 업데이트를 수행 하는 경우에도 업데이트 확인을 차단 해야 합니다. 이 항목의 앞부분에 나오는 "업데이트를 위한 사용자 인터페이스 제공"을 참조 하십시오.

 업데이트 확인을 차단하려면 애플리케이션 업데이트 대화 상자에서 **애플리케이션이 업데이트를 확인해야 함** 확인란의 선택을 취소합니다.

 배포 매니페스트에서 `<Subscription>` 태그를 제거하여 업데이트 확인을 차단할 수도 있습니다.

## <a name="permission-elevation-and-updates"></a>사용 권한 높이기 및 업데이트
 새 버전의 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션을 실행하는 데 이전 버전보다 높은 신뢰 수준이 필요할 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]에서 애플리케이션에 더 높은 신뢰 수준을 부여할지 묻는 메시지가 표시됩니다. 사용자가 더 높은 신뢰 수준 부여를 거절하면 업데이트가 설치되지 않습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]에서는 다음에 시작할 때 다시 사용자에게 애플리케이션을 설치할지 묻습니다. 업데이트가 필수로 표시되지 않은 경우 이때 더 높은 신뢰 수준을 부여하지 않도록 지정하면 이전 버전의 애플리케이션이 실행됩니다. 그러나 업데이트가 필수일 경우에는 사용자가 더 높은 신뢰 수준을 허용할 때까지 애플리케이션이 실행되지 않습니다.

 신뢰할 수 있는 애플리케이션 배포를 사용할 경우 신뢰 수준에 대한 메시지가 표시되지 않습니다. 자세한 내용은 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
 \<xref:System.Deployment.Application>
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce에서 애플리케이션 업데이트가 수행되는 방식](../deployment/how-clickonce-performs-application-updates.md)
- [방법: ClickOnce 응용 프로그램에 대 한 업데이트 관리](../deployment/how-to-manage-updates-for-a-clickonce-application.md)