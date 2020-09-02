---
title: 명령줄 스위치 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562278"
---
# <a name="adding-command-line-switches"></a>명령줄 스위치 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

devenv.exe 실행 될 때 VSPackage에 적용 되는 명령줄 스위치를 추가할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>스위치 이름과 해당 속성을 선언 하는 데 사용 합니다. 이 예제에서는 인수 없이 **Addcommandswitchpackage** 라는 VSPackage 라는 하위 클래스에 대해 MySwitch 스위치를 추가 하 고 VSPackage를 자동으로 로드 합니다.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 다음 표에는 명명 된 매개 변수가 나와 있습니다.  
  
 인수  
 스위치에 대 한 인수 개수입니다. "*" 또는 인수 목록 일 수 있습니다.  
  
 DemandLoad  
 VSPackage가 1로 설정 되어 있으면 자동으로 로드 하 고 그렇지 않으면 0으로 설정 합니다.  
  
 HelpString  
 **Devenv/?** 를 사용 하 여 표시할 문자열의 도움말 문자열 또는 리소스 ID입니다.  
  
 Name  
 스위치입니다.  
  
 PackageGuid  
 패키지의 GUID입니다.  
  
 인수의 첫 번째 값은 일반적으로 0 또는 1입니다. 특수 값 ' * '를 사용 하 여 명령줄의 전체 나머지가 인수 임을 나타낼 수 있습니다. 이는 사용자가 디버거 명령 문자열을 전달 해야 하는 디버깅 시나리오에 유용할 수 있습니다.  
  
 DemandLoad 값은 `true` (1) 또는 `false` (0) VSPackage가 자동으로 로드 되어야 함을 나타냅니다.  
  
 HelpString 값은 devenv/?에 표시 되는 문자열의 리소스 ID입니다. 도움말 표시. 이 값은 "#nnn" 형식 이어야 합니다. 여기서 nnn은 정수입니다. 리소스 파일의 문자열 값은 줄 바꿈 문자로 끝나야 합니다.  
  
 이름 값은 스위치의 이름입니다.  
  
 PackageGuid 값은이 스위치를 구현 하는 패키지의 GUID입니다. IDE는이 GUID를 사용 하 여 명령줄 스위치가 적용 되는 레지스트리의 VSPackage을 찾습니다.  
  
## <a name="retrieving-command-line-switches"></a>명령줄 스위치 검색  
 패키지가 로드 되 면 다음 단계를 완료 하 여 명령줄 스위치를 검색할 수 있습니다.  
  
1. VSPackage의 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> `QueryService` 에 대해를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> 하 여 인터페이스를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> .  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>을 호출 하 여 사용자가 입력 한 명령줄 스위치를 검색 합니다.  
  
   다음 코드에서는 MySwitch 명령줄 스위치가 사용자에 의해 입력 되었는지 확인 하는 방법을 보여 줍니다.  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 패키지가 로드 될 때마다 명령줄 스위치를 확인 하는 것은 사용자의 책임입니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef 유틸리티](../extensibility/internals/createpkgdef-utility.md)   
 [.pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
