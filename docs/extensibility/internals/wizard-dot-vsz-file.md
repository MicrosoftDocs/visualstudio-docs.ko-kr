---
title: 마법사 (. Vsz) 파일 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703318"
---
# <a name="wizard-vsz-file"></a>마법사(.Vsz) 파일

통합 개발 환경(IDE)은 .vsz 파일을 사용하여 마법사를 시작합니다. 이러한 .vsz 파일에는 IDE가 호출할 마법사와 마법사에 전달할 정보를 결정하는 데 사용하는 정보가 포함되어 있습니다.

.vsz 파일은 섹션이 없는 .ini 형식의 텍스트 파일의 버전입니다. IDE에 알려진 정보는 파일의 시작 부분에 저장됩니다. 이렇게 하면 IDE가 호출하는 마법사와 .vsz 파일에 있는 매개 변수 가 IDE에 전달됩니다. 파일의 나머지 부분에서는 마법사와 관련이 있고 IDE에서 수집하고 특정 마법사에 전달하는 매개 변수를 제공합니다.

다음 예제에서는 .vsz 파일의 내용을 보여 주며 있습니다.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

다음은 .vsz 파일의 부분입니다.

|부분|설명|
|----------|-----------------|
|VS 마법사|파일의 첫 번째 매개 변수는 템플릿 파일 형식의 버전 번호입니다. 이 버전 번호는 6.0, 7.0, 7.1 또는 8.0이어야 합니다. 다른 번호는 시작할 수 없으며 잘못된 형식 오류가 발생합니다.|
|마법사|이 필드에는 마법사의 OLE ProgID 또는 IDE에서 공동 생성하는 마법사의 CLSID의 GUID 문자열 표현이 포함되어 있습니다.|
|매개 변수|이러한 부품은 선택 사항입니다. 필요한 만큼 추가할 수 있습니다.|

이 매개 변수를 사용하면 .vsz 파일이 추가 사용자 지정 매개 변수를 마법사에 전달할 수 있습니다. 각 값은 변형 배열의 문자열 요소로 마법사에 전달됩니다. 자세한 내용은 [사용자 지정 매개 변수 를](../../extensibility/internals/custom-parameters.md)참조하십시오.

.vsz 파일에 기본 로캘 ID를 추가하려면 영어의 경우 xxxx가 로케일 ID인 경우 =xxxx를 지정합니다. `FALLBACK_LCID` `FALLBACK_LCID` 매개 변수가 정의되면 현재 ID를 찾을 수 없는 경우 마법사에서 제공된 대체 로캘 ID를 사용합니다.

## <a name="see-also"></a>참조

- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)
- [마법사](../../extensibility/internals/wizards.md)
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
