---
title: 사용자 지정 매개 변수 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708942"
---
# <a name="custom-parameters"></a>사용자 지정 매개 변수
사용자 지정 매개 변수는 마법사가 시작된 후 마법사의 작업을 제어합니다. 관련 *.vsz* 파일은 통합 개발 환경(IDE)에 의해 패키징되고 마법사가 시작될 때 문자열의 배열로 마법사에 전달되는 사용자 정의 매개 변수의 배열을 제공합니다. 그런 다음 마법사는 문자열 배열을 구문 분석하고 정보를 사용하여 마법사의 실제 작업을 제어합니다. 이러한 방식으로 마법사는 *.vsz* 파일의 내용에 따라 기능을 사용자 지정할 수 있습니다.

 반면 컨텍스트 매개 변수는 마법사가 시작될 때 프로젝트의 상태를 정의합니다. 자세한 내용은 [컨텍스트 매개 변수를](../../extensibility/internals/context-parameters.md)참조하십시오.

 다음은 사용자 지정 매개 변수가 있는 *.vsz* 파일의 예입니다.

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 *.vsz* 파일의 작성자가 매개 변수의 값을 추가합니다. 사용자가 **파일** 메뉴에서 **새 프로젝트** 또는 새 **항목 추가를** 선택하거나 **솔루션 탐색기에서**프로젝트를 마우스 오른쪽 단추로 클릭하여 IDE는 이러한 값을 문자열 배열로 수집합니다. 그런 다음 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> 플래그 집합을 사용하여 프로젝트의 메서드를 <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> 호출하고 프로젝트는 마법사를 실행하고 결과를 반환하는 메서드를 호출합니다.

 마법사는 문자열배열을 구문 분석하고 문자열에 대해 적절하게 작업합니다. 이러한 방식으로 사용자 지정 매개 변수를 구현하여 다양한 기능을 수행하는 마법사를 하나 만들 수 있습니다. 즉, 한 마법사에는 세 개의 다른 *.vsz* 파일이 있을 수 있습니다. 각 파일은 다양한 상황에서 마법사의 동작을 제어하기 위해 서로 다른 사용자 지정 매개 변수 집합을 전달합니다.

 자세한 내용은 [마법사(.vsz) 파일을 참조하십시오.](../../extensibility/internals/wizard-dot-vsz-file.md)

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [마법사](../../extensibility/internals/wizards.md)
- [마법사(.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
