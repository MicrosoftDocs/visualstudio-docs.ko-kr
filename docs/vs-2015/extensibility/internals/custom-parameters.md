---
title: 사용자 지정 매개 변수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a595861be835ec1aaa7079b3e3fe1962d5055e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154994"
---
# <a name="custom-parameters"></a>사용자 지정 매개 변수
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자 지정 매개 변수는 마법사가 시작 된 후의 마법사 작업을 제어 합니다. 관련 .vsz 파일은 IDE (통합 개발 환경)에서 패키지 되 고 마법사가 시작 될 때 마법사에 문자열 배열로 전달 되는 사용자 정의 매개 변수 배열을 제공 합니다. 그러면 마법사에서 문자열의 배열을 구문 분석 하 고 정보를 사용 하 여 마법사의 실제 작업을 제어 합니다. 이러한 방식으로 마법사는 .vsz 파일의 내용에 따라 기능을 사용자 지정할 수 있습니다.  
  
 반면, 컨텍스트 매개 변수는 마법사가 시작 될 때 프로젝트의 상태를 정의 합니다. 자세한 내용은 [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)를 참조 하세요.  
  
 다음은 사용자 지정 매개 변수를 포함 하는 .vsz 파일의 예입니다.  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz 파일의 작성자는 매개 변수 값을 추가 합니다. 사용자가 **새 프로젝트** 를 선택 하거나 파일 메뉴에서 **새 항목을 추가** 하거나 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 여 IDE는 이러한 값을 문자열 배열로 수집 합니다. 그런 다음 IDE는 플래그를 설정 하 여 프로젝트의 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> 하 고, 프로젝트는 <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> 마법사 실행을 담당 하 고 결과를 반환 하는 메서드를 호출 합니다.  
  
 이 마법사는 문자열의 배열을 구문 분석 하 고 문자열에 대해 적절 하 게 동작 합니다. 이러한 방식으로 사용자 지정 매개 변수를 구현 하 여 다양 한 기능을 수행 하는 마법사를 만들 수 있습니다. 즉, 한 마법사에는 세 개의 다른 .vsz 파일이 있을 수 있습니다. 각 파일은 다양 한 상황에서 마법사의 동작을 제어 하기 위해 서로 다른 사용자 지정 매개 변수 집합을 전달 합니다.  
  
 자세한 내용은 [Wizard (를 참조 하세요. .Vsz 파일](../../extensibility/internals/wizard-dot-vsz-file.md)입니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)   
 [마법사로](../../extensibility/internals/wizards.md)   
 [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
