---
title: 서비스 Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705494"
---
# <a name="service-essentials"></a>서비스 필수 항목
서비스는 두 Vspackage 사이의 계약입니다. 하나의 VSPackage는 다른 VSPackage에서 사용할 특정 인터페이스 집합을 제공 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자체는 다른 Vspackage에 서비스를 제공 하는 Vspackage의 컬렉션입니다.

 예를 들어, SVsActivityLog 서비스를 사용 하 여 활동 로그에 쓰는 데 사용할 수 있는 IVsActivityLog 인터페이스를 가져올 수 있습니다. 자세한 내용은 [방법: 활동 로그 사용](../../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 또한는 등록 되지 않은 몇 가지 기본 제공 서비스도 제공 합니다. Vspackage는 서비스 재정의를 제공 하 여 기본 제공 또는 다른 서비스를 대체할 수 있습니다. 서비스에 대 한 서비스 재정의는 하나만 허용 됩니다.

 서비스는 검색할 수 없습니다. 따라서 사용 하려는 서비스의 SID (서비스 식별자)를 알아야 하며, 제공 하는 인터페이스를 알고 있어야 합니다. 서비스에 대 한 참조 설명서에서는이 정보를 제공 합니다.

- 서비스를 제공 하는 Vspackage를 서비스 공급자 라고 합니다.

- 다른 Vspackage에 제공 되는 서비스를 글로벌 서비스 라고 합니다.

- 이러한 서비스를 구현 하는 VSPackage 사용할 수 있는 서비스 또는 만든 개체에만 사용할 수 있는 서비스를 로컬 서비스 라고 합니다.

- 다른 패키지에서 제공 하는 기본 제공 서비스 또는 서비스를 대체 하는 서비스를 서비스 재정의 라고 합니다.

- 서비스 또는 서비스 재정의는 요구에 따라 로드 됩니다. 즉, 서비스 공급자가 제공 하는 서비스가 다른 VSPackage에 의해 요청 될 때 로드 됩니다.

- 요청 시 로드를 지원 하기 위해 서비스 공급자는에 전역 서비스를 등록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. 자세한 내용은 [방법: 서비스 제공](../../extensibility/how-to-provide-a-service.md)을 참조 하세요.

- 서비스를 구한 후에는 [QueryInterface](/cpp/atl/queryinterface) (비관리 코드) 또는 캐스트 (관리 코드)를 사용 하 여 원하는 인터페이스를 가져옵니다. 예를 들면 다음과 같습니다.

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- 관리 코드는 해당 형식으로 서비스를 참조 하지만 비관리 코드는 해당 GUID로 서비스를 참조 합니다.

- 에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage를 로드할 때 서비스 공급자를 VSPackage에 전달 하 여 글로벌 서비스에 대 한 VSPackage 액세스를 제공 합니다. 이를 VSPackage의 "사이 팅" 이라고 합니다.

- Vspackage은 자신이 만드는 개체의 서비스 공급자 일 수 있습니다. 예를 들어, 폼은 색 서비스에 대 한 요청을 해당 프레임으로 보내 요청을에 전달할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- 깊게 중첩 되거나 전혀 배치 되지 않는 관리 되는 개체는 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 전역 서비스에 대 한 직접 액세스를 호출할 수 있습니다.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>GetGlobalService 사용

다른 방법으로는 이동 하지 않은 도구 창이 나 제어 컨테이너에서 서비스를 가져와야 하거나, 원하는 서비스를 알지 못하는 서비스 공급자와 함께 서비스를 가져와야 하는 경우도 있습니다. 예를 들어, 컨트롤 내에서 활동 로그에 쓸 수 있습니다. 이러한 시나리오와 기타 시나리오에 대 한 자세한 내용은 [방법: 서비스 문제 해결](../../extensibility/how-to-troubleshoot-services.md)을 참조 하세요.

정적 메서드를 호출 하 여 대부분의 Visual Studio 서비스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 는 패키지에서 파생 된 VSPackage가 처음으로 배치 될 때 초기화 되는 캐시 된 서비스 공급자에 의존 합니다. 이 조건에 만족 하거나 null 서비스에 대해 준비 해야 합니다.

다행히는 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 대부분의 시간 동안 제대로 작동 합니다.

- VSPackage가 다른 VSPackage만 알려진 서비스를 제공 하는 경우 서비스를 요청 하는 VSPackage는 서비스를 제공 하는 VSPackage가 로드 되기 전에 배치 됩니다.

- 도구 창이 VSPackage에서 생성 되는 경우 도구 창이 만들어지기 전에 VSPackage가 배치 됩니다.

- VSPackage에서 만든 도구 창에서 컨트롤 컨테이너를 호스팅하는 경우 컨트롤 컨테이너를 만들기 전에 VSPackage가 배치 됩니다.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>도구 창 또는 컨트롤 컨테이너 내에서 서비스를 가져오려면

- 생성자, 도구 창 또는 컨트롤 컨테이너에이 코드를 삽입 합니다.

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

    이 코드는 SVsActivityLog 서비스를 가져와 활동 로그에 쓰는 데 사용할 수 있는 IVsActivityLog 인터페이스로 캐스팅 합니다. 예제는 [방법: 활동 로그 사용](../../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [사용 가능한 서비스 목록](../../extensibility/internals/list-of-available-services.md)
- [서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)
- [캐스팅 및 형식 변환](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [캐스팅](/cpp/cpp/casting)
