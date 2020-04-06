---
title: 명령줄 스위치 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740171"
---
# <a name="add-command-line-switches"></a>명령줄 스위치 추가
*devenv.exe가* 실행될 때 VSPackage에 적용되는 명령줄 스위치를 추가할 수 있습니다. 스위치 <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> 및 해당 속성의 이름을 선언하는 데 사용합니다. 이 예제에서는 인수없이 VSPackage가 자동으로 로드된 **ADDCommandSwitchPackage라는** VSPackage의 하위 클래스에 대해 MySwitch 스위치가 추가됩니다.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 명명된 매개 변수는 다음 설명에 나와 있습니다.

||||
|-|-|-|-|
| 매개 변수 | 설명|
| 인수 | 스위치에 대한 인수 수입니다. "*" 또는 인수 목록일 수 있습니다. |
| 수요 로드 | VSPackage를 1로 설정한 경우 자동으로 로드하고 그렇지 않으면 0으로 설정합니다. |
| Helpstring | **devenv /?**. |
| 이름 | 스위치입니다. |
| 패키지 가드 | 패키지의 GUID입니다. |

 인수의 첫 번째 값은 일반적으로 0 또는 1입니다. '*'의 특수 값을 사용하여 명령줄의 나머지 전체가 인수임을 나타낼 수 있습니다. 이 기능은 사용자가 디버거 명령 문자열을 전달해야 하는 시나리오를 디버깅하는 데 유용할 수 있습니다.

 수요로드 값은 `true` (1) `false` 또는 (0)이며 VS패키지가 자동으로 로드되어야 음을 나타냅니다.

 HelpString 값은 **devenv /?** 도움말 표시. 이 값은 nnn이 정수인 "#nnn" 형식이어야 합니다. 리소스 파일의 문자열 값은 새 줄 문자로 끝나야 합니다.

 이름 값은 스위치의 이름입니다.

 PackageGuid 값은 이 스위치를 구현하는 패키지의 GUID입니다. IDE는 이 GUID를 사용하여 명령줄 스위치가 적용되는 레지스트리에서 VSPackage를 찾습니다.

## <a name="retrieve-command-line-switches"></a>명령줄 스위치 검색
 패키지가 로드되면 다음 단계를 완료하여 명령줄 스위치를 검색할 수 있습니다.

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage 구현에서 인터페이스를 `QueryService` 얻으려면 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>

2. 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> 사용자가 입력한 명령줄 스위치를 검색합니다.

   다음 코드는 사용자가 MySwitch 명령줄 스위치를 입력했는지 여부를 확인하는 방법을 보여 주며 다음과 같은 방법을 보여 주며 다음과 같은 방법을 보여 주며,

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 패키지가 로드될 때마다 명령줄 스위치를 확인하는 것은 사용자의 책임입니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)
- [만들기PkgDef 유틸리티](../extensibility/internals/createpkgdef-utility.md)
- [. Pkgdef 파일](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
