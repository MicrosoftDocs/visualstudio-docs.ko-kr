---
title: Interop 어셈블리 명령 처리기를 등록 하는 중 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfff8e4e6cc8ba3974ec70e6466b25e9ff7432e4
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012050"
---
# <a name="registering-interop-assembly-command-handlers"></a>Interop 어셈블리 명령 처리기를 등록
VSPackage는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (통합 개발 환경)가 해당 명령을 제대로 라우팅하도록에 등록 해야 합니다.

 레지스트리는 수동으로 편집 하거나 등록자 (.rgs) 파일을 사용 하 여 업데이트할 수 있습니다. 자세한 내용은 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)을 참조하세요.

 MPF (관리 되는 패키지 프레임 워크)는 클래스를 통해이 기능을 제공 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> .

- [명령 테이블 형식 참조](/previous-versions/bb164647(v=vs.100)) 리소스는 관리 되지 않는 위성 UI dll에 있습니다.

## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage의 명령 처리기 등록
 UI (사용자 인터페이스) 기반 명령의 처리기 역할을 하는 VSPackage에는 VSPackage 뒤에 이름이 지정 된 레지스트리 항목이 필요 합니다 `GUID` . 이 레지스트리 항목은 VSPackage UI 리소스 파일의 위치와 해당 파일 내의 메뉴 리소스를 지정 합니다. 레지스트리 항목 자체는 HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ *\<Version>* \menus에 있습니다 *\<Version>* . 여기서은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 9.0입니다.

> [!NOTE]
> HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio의 루트 경로는 \\ *\<Version>* 셸이 초기화 될 때 대체 루트를 사용 하 여 재정의할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 루트 경로에 대 한 자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)를 참조 하세요.

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 리소스 레지스트리 항목
 레지스트리 항목의 구조는 다음과 같습니다.

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> 은 {XXXXXX-xxxx- `GUID` XXXXXXXXX} 형식으로 된 VSPackage의입니다.

 *\<Resource Information>* 는 쉼표로 구분 된 세 개의 요소로 구성 됩니다. 이러한 요소는 순서 대로 다음과 같습니다.

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 다음 표에서는의 필드에 대해 설명 합니다 \<*Resource Information*> .

| 요소 | Description |
|---------------------------| - |
| \<*Path to Resource DLL*> | 이는 메뉴 리소스를 포함 하는 리소스 DLL의 전체 경로 이거나 비어 있습니다 .이 경로는 VSPackage의 리소스 DLL이 사용 됨을 나타냅니다 (VSPackage 자체가 등록 된 패키지 하위 키에 지정 된 대로).<br /><br /> 이 필드는 비워 둘 수 있습니다. |
| \<*Menu Resource ID*> | `CTMENU`VSPackage에 대 한 모든 UI 요소를 포함 하는 리소스의 리소스 ID입니다 [.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Menu Version*> | 리소스의 버전으로 사용 되는 숫자입니다 `CTMENU` . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는이 값을 사용 하 여 리소스의 콘텐츠를 `CTMENU` 모든 리소스의 캐시와 다시 병합 해야 하는지 여부를 결정 `CTMENU` 합니다. 다시 병합은 devenv setup 명령을 실행 하 여 트리거됩니다.<br /><br /> 처음에는이 값을 1로 설정 하 고 리소스의 모든 변경 후 `CTMENU` 와 다시 병합이 발생 하기 전에 증가 해야 합니다. |

### <a name="example"></a>예
 다음은 몇 가지 리소스 항목의 예입니다.

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>참고 항목
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Interop 어셈블리를 사용하는 명령 및 메뉴](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)