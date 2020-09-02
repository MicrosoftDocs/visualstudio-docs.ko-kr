---
title: 격리 된 셸 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204609"
---
# <a name="elements-of-the-isolated-shell"></a>격리 셸의 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

격리 된 셸 응용 프로그램의 레지스트리 설정, 런타임 설정 및 응용 프로그램 진입점과 해당 .pkgdef 및. .pkgundef 파일을 수정할 수 있습니다.  
  
## <a name="registry-settings"></a>레지스트리 설정  
 .Pkgdef 및 .pkgundef 파일은 모두 격리 된 셸 응용 프로그램에 대 한 레지스트리 설정을 수정 합니다. 응용 프로그램이 실행 될 때 레지스트리 설정은 다음 순서로 정의 됩니다.  
  
 응용 프로그램이 실행 될 때 레지스트리 설정은 다음 순서로 정의 됩니다.  
  
1. 응용 프로그램에 대 한 레지스트리 키가 생성 됩니다.  
  
2. 레지스트리는 지정 된 키와 항목을 정의 하 여 응용 프로그램의 .pkgdef 파일에서 업데이트 됩니다.  
  
3. 응용 프로그램의 일부인 모든 패키지에 대해 해당 패키지의 .pkgdef 파일에서 레지스트리가 업데이트 됩니다. 각 패키지는 \\ 패키지에 대 한 $RootKey $ \packages {*vsPackageGuid*} 키로 응용 프로그램의 .pkgdef 파일에 정의 됩니다.  
  
4. AppEnvConfig .pkgdef 및 BaseConfig의 *Visual STUDIO SDK 설치 경로*\Common7\IDE\ShellExtensions\Platform 디렉터리에서 레지스트리가 업데이트 됩니다. 이러한 파일은 Visual Studio의 일부 이며 Visual Studio Shell (격리 모드) 재배포 가능 패키지에도 포함 되어 있습니다.  
  
5. 레지스트리는 지정 된 키와 항목을 제거 하 여 응용 프로그램의 .pkgundef 파일에서 업데이트 됩니다.  
  
## <a name="run-time-settings"></a>런타임 설정  
 사용자가 격리 된 셸 응용 프로그램을 시작 하면 Visual Studio 셸의 시작 진입점을 호출 합니다. 응용 프로그램 설정은 다음과 같이 응용 프로그램을 시작할 때 정의 됩니다.  
  
1. Visual Studio shell은 응용 프로그램 레지스트리에서 특정 키를 확인 합니다. 시작 진입점에 대 한 호출에서 키에 대 한 설정이 지정 된 경우 해당 값은 레지스트리의 값을 재정의 합니다.  
  
2. 레지스트리와 진입점 매개 변수 모두 설정 값을 지정 하지 않으면 설정의 기본값이 사용 됩니다.  
  
   사용자가 명령줄에서 응용 프로그램을 시작 하면 모든 명령줄 스위치가 Visual Studio 셸에 전달 되어 Devenv와 동일한 방식으로 처리 됩니다. Devenv 스위치에 대 한 자세한 내용은 [VSPackage 개발용](../extensibility/devenv-command-line-switches-for-vspackage-development.md) [devenv](../ide/reference/devenv-command-line-switches.md) 명령줄 스위치 및 devenv 명령줄 스위치를 참조 하세요. 패키지에서 명령줄 스위치를 등록 하는 방법에 대 한 자세한 내용은 [명령줄 스위치 추가](../extensibility/adding-command-line-switches.md)를 참조 하세요.  
  
## <a name="the-start-entry-point"></a>시작 진입점입니다.  
 Appenvstub.dll 파일에는 isolated 셸에 액세스 하기 위한 진입점이 포함 되어 있습니다. 응용 프로그램이 시작 되 면 Appenvstub.dll 시작 진입점을 호출 합니다.  
  
 시작 진입점에 전달 되는 마지막 매개 변수의 값을 변경 하 여 응용 프로그램의 동작을 변경할 수 있습니다. 자세한 내용은 [격리 된 셸 진입점 매개 변수 (c + +)](../extensibility/isolated-shell-entry-point-parameters-cpp.md)를 참조 하세요.  
  
## <a name="the-vsct-file"></a>여. Vsct 파일  
 . Vsct 파일을 사용 하면 응용 프로그램에서 사용할 수 있는 표준 Visual Studio UI 요소를 지정할 수 있습니다. 자세한 내용은을 참조 하십시오 [. Vsct 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>여. .Pkgundef 파일  
 Visual Studio가 이미 설치 된 컴퓨터에 응용 프로그램을 설치 하는 경우 응용 프로그램에 대 한 Visual Studio 레지스트리 항목의 복사본이 생성 됩니다. 기본적으로 응용 프로그램은 컴퓨터에 이미 설치 되어 있는 Vspackage를 사용 합니다. .Pkgundef 파일을 사용 하면 응용 프로그램에서 Visual Studio 셸의 특정 요소 또는 확장 프로그램을 제거 하기 위해 레지스트리 항목을 제외할 수 있습니다. 자세한 내용은을 참조 하십시오 [. .Pkgundef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 .Pkgundef 파일을 사용 하면 응용 프로그램에서 Visual Studio 셸의 특정 요소 또는 확장 프로그램을 제거 하기 위해 레지스트리 항목을 제외할 수 있습니다. 자세한 내용은을 참조 하십시오 [. .Pkgundef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 제외할 수 있는 패키지 Guid 집합은 [Visual Studio 기능의 패키지 guid](../extensibility/package-guids-of-visual-studio-features.md)에 나열 됩니다.  
  
## <a name="the-pkgdef-file"></a>여. .Pkgdef 파일  
 .Pkgdef 파일을 사용 하면 응용 프로그램 설치 시 설정 된 응용 프로그램에 대 한 레지스트리 항목을 정의할 수 있습니다. .Pkgdef 파일에 대 한 설명과 Visual Studio 셸에서 사용 하는 레지스트리 항목 목록은를 참조 하십시오 [. .Pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>대체 문자열  
 .Pkgdef 및 .pkgundef 파일에 사용 된 대체 문자열은 [에서 사용 되는 대체 문자열에 나열 됩니다. .Pkgdef 및입니다. .Pkgundef 파일](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>기타 설정  
 격리 셸 응용 프로그램이 Microsoft.VisualStudio.GraphModel.dll에 종속 된 경우 다음 바인딩 리디렉션을 격리 된 셸 응용 프로그램의 .config 파일에 추가 해야 합니다.  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
