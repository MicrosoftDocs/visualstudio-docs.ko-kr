---
title: '방법: 서비스 문제 해결 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710744"
---
# <a name="how-to-troubleshoot-services"></a>방법: 서비스 문제 해결
서비스를 받으려고 할 때 발생할 수 있는 몇 가지 일반적인 문제가 있습니다.

- 서비스에 등록되지 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]않았습니다.

- 서비스는 서비스 유형이 아닌 인터페이스 유형에 의해 요청됩니다.

- 서비스를 요청하는 VSPackage가 사이트에 지정되지 않았습니다.

- 잘못된 서비스 공급자가 사용됩니다.

  요청된 서비스를 얻을 수 없는 경우 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null을 반환하는 호출입니다. 서비스를 요청한 후에는 항상 null을 테스트해야 합니다.

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>서비스 문제 해결

1. 시스템 레지스트리를 검사하여 서비스가 올바르게 등록되었는지 확인합니다. 자세한 내용은 [서비스 제공 방법을](../extensibility/how-to-provide-a-service.md)참조하십시오.

    다음 *.reg* 파일 조각은 SVsTextManager 서비스를 등록하는 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    위의 예에서 버전 번호는 12.0 또는 14.0과 같은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]버전이며, 키 {F5E7E71D-1401-11d1-883B-0000F87579D2}는 서비스의 서비스 식별자(SID)이며, SVsTextManager 및 기본값 {F5E7E720-1401-11d1-883B-0000F87579D2}는 서비스를 제공하는 텍스트 관리자 VSPackage의 패키지 GUID입니다.

2. GetService를 호출할 때 인터페이스 유형이 아닌 서비스 형식을 사용합니다. 에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Package> 서비스를 요청할 때 형식에서 GUID를 추출합니다. 다음과 같은 조건이 있는 경우 서비스를 찾을 수 없습니다.

   1. 인터페이스 형식은 서비스 형식 대신 GetService에 전달됩니다.

   2. 인터페이스에 명시적으로 할당된 GUID가 없습니다. 따라서 시스템은 필요에 따라 개체에 대한 기본 GUID를 만듭니다.

3. 서비스를 요청하는 VSPackage가 사이트에 지정되어 있는지 확인합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]을 호출하기 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>전에 생성한 후 VSPackage를 사이트합니다.

    서비스가 필요한 VSPackage 생성자에 코드가 있는 경우 `Initialize` 메서드로 이동합니다.

4. 올바른 서비스 공급자를 사용하고 있는지 확인합니다.

    모든 서비스 제공업체가 같은 것은 아닙니다. 도구 창을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 전달하는 서비스 공급자는 VSPackage에 전달하는 공급자와 다릅니다. 도구 창 서비스 공급자는 에 대해 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>알고 있지만 에 대해 알지 못합니다. 도구 창 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 내에서 VSPackage 서비스 공급자를 호출할 수 있습니다.

    도구 창에서 사용자 컨트롤 또는 기타 컨트롤 컨테이너를 호스트하는 경우 컨테이너는 Windows 구성 요소 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 모델에 의해 사이트화되고 서비스에 액세스할 수 없습니다. <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 호출하여 VSPackage 서비스 공급자를 제어 컨테이너 내에서 가져옵니다.

## <a name="see-also"></a>참조
- [이용 가능한 서비스 목록](../extensibility/internals/list-of-available-services.md)
- [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)
- [서비스 필수 요소](../extensibility/internals/service-essentials.md)
