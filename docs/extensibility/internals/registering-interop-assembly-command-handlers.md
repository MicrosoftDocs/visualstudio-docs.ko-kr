---
title: 인터롭 어셈블리 커맨드 핸들러 등록 | 마이크로 소프트 문서
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
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705856"
---
# <a name="registering-interop-assembly-command-handlers"></a>Interop 어셈블리 명령 처리기를 등록
통합 개발 환경(IDE)이 명령을 올바르게 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 라우팅할 수 있도록 VSPackage에 등록해야 합니다.

 레지스트리는 수동 편집 또는 등록기관(.rgs) 파일을 사용하여 업데이트할 수 있습니다. 자세한 내용은 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)을 참조하세요.

 MPF(관리되는 패키지 프레임워크)는 클래스를 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 통해 이 기능을 제공합니다.

- [명령 테이블 형식 참조](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) 리소스는 관리되지 않는 위성 UI dlls에 있습니다.

## <a name="command-handler-registration-of-a-vspackage"></a>VS패키지의 명령 처리기 등록
 사용자 인터페이스(UI) 기반 명령에 대한 처리기 역할을 하는 VSPackage에는 VSPackage `GUID`의 이름을 따서 명명된 레지스트리 항목이 필요합니다. 이 레지스트리 항목은 VSPackage의 UI 리소스 파일의 위치와 해당 파일 내의 메뉴 리소스를 지정합니다. 레지스트리 항목 자체는 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<버전>* \메뉴 아래에 있으며, * \<여기서 버전>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 버전입니다 .

> [!NOTE]
> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<버전>* 루트 경로를 셸이 초기화될 때 대체 루트로 재정의할 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 루트 경로에 대한 자세한 내용은 [VS패키지 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)를 참조하십시오.

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 리소스 레지스트리 항목
 레지스트리 항목의 구조는 다음과 같은 것입니다.

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` {XXXXXX-XXXX-XXXX-XxxXXX-XXXXXX-XXXXXXXXXXXXXXX}의 VSPackage입니다.

 리소스 정보>쉼표로 구분된 세 가지 요소로 구성됩니다. * \<* 이러한 요소는 순서대로 다음과 같습니다.

 \<*리소스 DLL*> \<경로, 메뉴 \<리소스 *ID*>, 메뉴 *버전*>

 다음 표는 \< *리소스 정보*> 필드를 설명합니다.

| 요소 | Description |
|---------------------------| - |
| \<*리소스 DLL로의 경로*> | 메뉴 리소스를 포함 하거나 이 메뉴 리소스를 포함 하는 리소스 DLL에 대 한 전체 경로 또는이 비어 있는 남아, VSPackage의 리소스 DLL을 사용 하는 것을 나타내는 (VSPackage 자체가 등록 된 패키지 하위 키에 지정 된 대로).<br /><br /> 이 필드를 비워 두는 것이 관례입니다. |
| \<*메뉴 리소스 ID*> | [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) 파일에서 `CTMENU` 컴파일된 VSPackage의 모든 UI 요소를 포함하는 리소스의 리소스 ID입니다. |
| \<*메뉴 버전*> | 리소스의 버전으로 사용되는 숫자입니다. `CTMENU` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]이 값을 사용하여 `CTMENU` 모든 `CTMENU` 리소스의 캐시를 사용하여 리소스의 내용을 다시 병합해야 하는지 여부를 결정합니다. devenv 설정 명령을 실행하여 다시 병합이 트리거됩니다.<br /><br /> 이 값은 처음에 1로 설정하고 `CTMENU` 리소스의 모든 변경 후 및 재병합이 발생하기 전에 증분되어야 합니다. |

### <a name="example"></a>예제
 다음은 몇 가지 리소스 항목의 예입니다.

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>참조
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Interop 어셈블리를 사용하는 명령 및 메뉴](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
