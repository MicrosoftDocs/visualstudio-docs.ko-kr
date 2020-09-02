---
title: 마법사 (. .Vsz 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab1adde4c7018f136f47769e16a8ce2fedf72c93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687659"
---
# <a name="wizard-vsz-file"></a>마법사(.Vsz) 파일
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE (통합 개발 환경)는 .vsz 파일을 사용 하 여 마법사를 시작 합니다. 이러한 .vsz 파일에는 IDE에서 호출할 마법사와 마법사에 전달할 정보를 결정 하는 데 사용 하는 정보가 포함 되어 있습니다.  
  
 .Vsz 파일은 섹션이 없는 .ini 형식의 텍스트 파일 버전입니다. IDE에 알려진 정보는 파일의 시작 부분에 저장 됩니다. Ide에서 호출 하는 마법사와 IDE에 전달할 .vsz 파일에 있는 매개 변수의 링크를 제공 합니다. 파일의 나머지 부분에서는 마법사와 관련 된 매개 변수를 제공 하며 IDE에서 수집 하 여 특정 마법사에 전달 합니다.  
  
 다음 예제에서는 .vsz 파일의 내용을 보여 줍니다.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 다음은 .vsz 파일의 일부입니다.  
  
|부분|설명|  
|----------|-----------------|  
|VSWizard|파일의 첫 번째 매개 변수는 템플릿 파일 형식의 버전 번호입니다. 이 버전 번호는 6.0, 7.0, 7.1 또는 8.0 이어야 합니다. 다른 숫자는 시작할 수 없으며 잘못 된 형식 오류가 발생 합니다.|  
|마법사|이 필드에는 마법사의 OLE ProgID 또는 IDE에서 공동으로 생성 되는 마법사의 CLSID에 대 한 GUID 문자열 표현이 포함 되어 있습니다.|  
|매개 변수|이러한 부분은 선택 사항입니다. 필요한 만큼 추가할 수 있습니다.|  
  
 매개 변수를 사용 하면 .vsz 파일에서 마법사에 추가 사용자 지정 매개 변수를 전달할 수 있습니다. 각 값은 마법사에 변형 배열의 문자열 요소로 전달 됩니다. 자세한 내용은 [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)를 참조 하세요. 사용자 지정 마법사 개발에서 .vsz 파일을 사용 하는 방법에 대 한 자세한 내용은을 참조 하십시오 [. .Vsz 파일 (프로젝트 컨트롤)](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 기본 로캘 ID를 .vsz 파일에 추가 하려면 `FALLBACK_LCID` = xxxx를 지정 합니다. 여기서 xxxx는 로캘 ID (예: 영어의 경우 1033)입니다. `FALLBACK_LCID`매개 변수가 정의 된 경우 현재 ID가 없는 경우 마법사에서 제공 된 대체 (fallback) 로캘 ID를 사용 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)   
 [마법사로](../../extensibility/internals/wizards.md)   
 [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
