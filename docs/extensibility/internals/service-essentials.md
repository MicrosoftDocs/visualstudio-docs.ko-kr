---
title: 서비스 필수 정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8817ca48ff0a3f44a973986a173e647ce89c662c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301634"
---
# <a name="service-essentials"></a>서비스 필수 항목
서비스는 두 VSPackage 간의 계약입니다. 한 VSPackage는 다른 VSPackage에서 사용할 특정 인터페이스 집합을 제공합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]은 다른 VSPackage에 서비스를 제공하는 VSPackage의 모음입니다.

 예를 들어 SVsActivityLog 서비스를 사용하여 활동 로그에 쓰는 데 사용할 수 있는 IVsActivityLog 인터페이스를 가져올 수 있습니다. 자세한 내용은 [사용 방법: 활동 로그를 사용](../../extensibility/how-to-use-the-activity-log.md)하 여 참조 하십시오.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]또한 등록되지 않은 일부 기본 제공 서비스를 제공합니다. VSPackage는 서비스 재정의를 제공하여 기본 제공 또는 기타 서비스를 대체할 수 있습니다. 모든 서비스에 대해 하나의 서비스 재정의만 허용됩니다.

 서비스에는 검색 가능성이 없습니다. 따라서 사용 하려는 서비스의 서비스 식별자 (SID)를 알고 있어야 합니다 및 제공 하는 인터페이스를 알고 있어야 합니다. 서비스에 대한 참조 설명서는 이 정보를 제공합니다.

- 서비스를 제공하는 VS패키지를 서비스 공급자라고 합니다.

- 다른 VSPackage에 제공되는 서비스를 전역 서비스라고 합니다.

- 이를 구현하는 VSPackage 또는 생성하는 모든 개체에서만 사용할 수 있는 서비스를 로컬 서비스라고 합니다.

- 다른 패키지에서 제공하는 기본 제공 서비스 또는 서비스를 대체하는 서비스를 서비스 재정의라고 합니다.

- 서비스 또는 서비스 재정의는 요청 시 로드됩니다.

- 온디맨드 로드를 지원하기 위해 서비스 공급자는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 글로벌 서비스를 등록합니다. 자세한 내용은 [서비스 제공 방법을](../../extensibility/how-to-provide-a-service.md)참조하십시오.

- 서비스를 얻은 후 [QueryInterface(관리되지](/cpp/atl/queryinterface) 않는 코드) 또는 캐스팅(관리되는 코드)을 사용하여 원하는 인터페이스를 가져옵니다.

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- 관리되는 코드는 해당 형식별로 서비스를 참조하는 반면 관리되지 않는 코드는 GUID에 의한 서비스를 나타냅니다.

- VSPackage를 로드하는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage에 서비스 공급자를 전달하여 VSPackage에 전역 서비스에 대한 액세스 권한을 부여합니다. 이를 VSPackage를 "앉기"라고 합니다.

- VSPackage는 만드는 개체에 대한 서비스 공급자가 될 수 있습니다. 예를 들어 양식은 해당 프레임에 색상 서비스에 대한 요청을 보낼 수 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]있으며, 이 요청을 에 전달할 수 있습니다.

- 깊이 중첩되거나 전혀 사이트되지 않은 관리되는 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 개체는 전역 서비스에 직접 액세스하도록 요청할 수 있습니다.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>겟글로벌서비스 사용

경우에 따라 사이트되지 않은 도구 창 또는 제어 컨테이너에서 서비스를 받아야 하거나 원하는 서비스에 대해 모르는 서비스 공급자와 함께 사이트를 지정해야 할 수도 있습니다. 예를 들어 컨트롤 내에서 활동 로그에 쓸 수 있습니다. 이러한 시나리오 및 기타 시나리오에 대한 자세한 내용은 [서비스 문제 해결 방법을 참조하세요.](../../extensibility/how-to-troubleshoot-services.md)

정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드를 호출하여 대부분의 Visual Studio 서비스를 얻을 수 있습니다.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>은 패키지에서 파생된 VSPackage가 처음 사이트에 지정될 때 초기화되는 캐시된 서비스 공급자에 의존합니다. 이 조건이 충족되도록 보장하거나 null 서비스에 대비해야 합니다.

다행히도 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 대부분의 경우 올바르게 작동합니다.

- VSPackage가 다른 VSPackage에만 알려진 서비스를 제공하는 경우 서비스를 제공하는 VSPackage가 로드되기 전에 서비스를 요청하는 VSPackage가 사이트에 지정됩니다.

- VSPackage에 의해 도구 창을 만든 경우 VSPackage는 도구 창을 작성하기 전에 사이트가 됩니다.

- VSPackage에서 만든 도구 창에서 컨트롤 컨테이너를 호스팅하는 경우 VSPackage는 컨트롤 컨테이너를 생성하기 전에 호스팅됩니다.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>도구 창 또는 제어 컨테이너 내에서 서비스를 받으려면

- 생성자, 도구 창 또는 제어 컨테이너에 이 코드를 삽입합니다.

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    이 코드는 SVsActivityLog 서비스를 가져오고 활동 로그에 쓰는 데 사용할 수 있는 IVsActivityLog 인터페이스로 캐스팅합니다. 예를 들어 사용 [방법: 활동 로그를 사용합니다.](../../extensibility/how-to-use-the-activity-log.md)

## <a name="see-also"></a>참고 항목

- [사용 가능한 서비스 목록](../../extensibility/internals/list-of-available-services.md)
- [서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)
- [캐스팅 및 유형 변환](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [캐스팅](/cpp/cpp/casting)