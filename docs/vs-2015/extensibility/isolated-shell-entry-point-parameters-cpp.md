---
title: 격리 된 셸 진입점 매개 변수 (c + +) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842139"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>격리 셸 진입점 매개 변수(C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio shell 기반 응용 프로그램이 시작 되 면 Visual Studio 셸의 시작 진입점을 호출 합니다. 셸의 시작 진입점에 대 한 호출에서 다음 설정을 재정의할 수 있습니다. 각 설정에 대 한 설명은를 참조 하십시오 [. .Pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- Defaul% Mepage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- 솔루션 Fileext  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Visual Studio Shell 격리 템플릿은 *solutionName*원본 파일을 만듭니다. 여기서 *solutionName* 는 응용 프로그램의 솔루션 이름입니다. 이 파일은 응용 프로그램의 주 진입점 _tWinMain 함수를 정의 합니다. 이 함수는 셸의 시작 진입점을 호출 합니다.  
  
  응용 프로그램이 시작 될 때 이러한 설정을 변경 하 여 응용 프로그램의 동작을 변경할 수 있습니다.  
  
## <a name="parameters"></a>매개 변수  
 Visual Studio shell의 시작 진입점은 5 개의 매개 변수를 정의 합니다. 처음 네 개의 매개 변수를 변경 하지 마십시오. 다섯 번째 매개 변수는 설정 재정의 목록을 사용 합니다. 셸의 시작 진입점은 응용 프로그램의 주 진입점에서 호출 됩니다.  
  
 셸의 시작 진입점에는 다음과 같은 시그니처가 있습니다.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 응용 프로그램 설정을 재정의 하지 않으려면 설정 재정의 매개 변수의 값을 null 포인터로 둡니다.  
  
 하나 이상의 설정을 재정의 하려면 재정의할 설정이 포함 된 유니코드 문자열을 전달 합니다. 문자열은 이름-값 쌍의 세미콜론으로 구분 된 목록입니다. 각 쌍에는 재정의할 설정의 이름, 등호 (=), 설정에 적용할 값이 차례로 포함 됩니다.  
  
> [!NOTE]
> 유니코드 문자열에 공백을 포함 하지 마십시오.  
  
 부울 설정의 경우 다음 문자열은 true 값을 나타냅니다. 다른 모든 문자열은 false 값을 나타냅니다. 이러한 문자열은 대/소문자를 구분 하지 않습니다.  
  
- \+  
  
- 1  
  
- -1  
  
- On  
  
- true  
  
- 예  
  
## <a name="example"></a>예제  
 추가 기능을 사용 하지 않도록 설정 하 고 응용 프로그램의 기본 프로젝트 위치를 변경 하려면 마지막 매개 변수를 "AddinsAllowed = false; DefaultProjectsLocation =%USERPROFILE%\temp"로 설정 하면 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [격리 셸 사용자 지정](../extensibility/customizing-the-isolated-shell.md)   
 [.pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
