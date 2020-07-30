---
title: '방법: 서비스 문제 해결 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bfbe4b11c22d6cfd147783f9fb662843cf57fe9
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234954"
---
# <a name="how-to-troubleshoot-services"></a>방법: 서비스 문제 해결
서비스를 가져오려고 할 때 발생할 수 있는 몇 가지 일반적인 문제는 다음과 같습니다.

- 서비스가에 등록 되지 않았습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- 서비스는 서비스 유형이 아닌 인터페이스 유형에 의해 요청 됩니다.

- 서비스를 요청 하는 VSPackage가 배치 되지 않았습니다.

- 잘못 된 서비스 공급자가 사용 되었습니다.

  요청 된 서비스를 가져올 수 없는 경우에 대 한 호출은 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null을 반환 합니다. 서비스를 요청한 후에는 항상 null을 테스트 해야 합니다.

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>서비스 문제를 해결 하려면

1. 시스템 레지스트리를 검사 하 여 서비스가 올바르게 등록 되었는지 확인 합니다. 자세한 내용은 [방법: 서비스 제공](../extensibility/how-to-provide-a-service.md)을 참조 하세요.

    다음 *.reg* 파일 조각은 SVsTextManager 서비스를 등록 하는 방법을 보여 줍니다.

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    위의 예제에서 버전 번호는 버전 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (예: 12.0 또는 14.0)이 고, 키 {F5E7E71D-1401-11d1-883B-0000F87579D2}는 서비스의 서비스 식별자 (SID)이 고, SVsTextManager 이며, 기본값 {F5E7E720-1401-11d1-883B-0000F87579D2}은 서비스를 제공 하는 텍스트 관리자 VSPackage의 패키지 GUID입니다.

2. GetService를 호출할 때 인터페이스 형식이 아닌 서비스 유형을 사용 합니다. 에서 서비스를 요청할 때 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 는 <xref:Microsoft.VisualStudio.Shell.Package> 형식에서 GUID를 추출 합니다. 다음 조건이 충족 되 면 서비스를 찾을 수 없습니다.

   1. 인터페이스 형식은 서비스 형식 대신 GetService에 전달 됩니다.

   2. 인터페이스에 명시적으로 할당 된 GUID가 없습니다. 따라서 시스템은 필요에 따라 개체에 대 한 기본 GUID를 만듭니다.

3. 서비스를 요청 하는 VSPackage가 배치 되었는지를 확인할 수 있습니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]를 구성 하 고를 호출 하기 전에 VSPackage를 사이트에 만듭니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    서비스를 필요로 하는 VSPackage 생성자에 코드가 있는 경우이를 `Initialize` 메서드로 이동 합니다.

4. 올바른 서비스 공급자를 사용 하 고 있는지를 알고 있어야 합니다.

    일부 서비스 공급자가 동일 하지는 않습니다. 도구 창에 전달 하는 서비스 공급자는 VSPackage에 전달 하는 공급자와 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 다릅니다. 도구 창 서비스 공급자는에 대해 알고 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 있지만에 대해 알지 못합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>을 호출 하 여 도구 창 내에서 VSPackage 서비스 공급자를 가져올 수 있습니다.

    도구 창이 사용자 정의 컨트롤 또는 다른 컨트롤 컨테이너를 호스트 하는 경우 컨테이너는 Windows 구성 요소 모델에 의해 배치 되며 어떤 서비스에도 액세스할 수 없습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>를 호출 하 여 컨트롤 컨테이너 내에서 VSPackage 서비스 공급자를 가져올 수 있습니다.

## <a name="see-also"></a>참고 항목
- [사용 가능한 서비스 목록](../extensibility/internals/list-of-available-services.md)
- [사용 및 서비스 제공](../extensibility/using-and-providing-services.md)
- [서비스 essentials](../extensibility/internals/service-essentials.md)
- [Visual Studio 문제 해결](/troubleshoot/visualstudio/welcome-visual-studio/)