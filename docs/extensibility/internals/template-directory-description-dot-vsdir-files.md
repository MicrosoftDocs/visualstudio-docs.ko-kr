---
title: 템플릿 디렉터리 설명 (. Vsdir) 파일 | Microsoft Docs
description: 템플릿 디렉터리 설명 파일을 사용 하 여 Visual Studio IDE에서 프로젝트와 연결 된 폴더, .vsz 파일 및 템플릿을 표시 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edc4b4bcfe1ac1a85524517ba467e207a792e3cd
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877730"
---
# <a name="template-directory-description-vsdir-files"></a>템플릿 디렉터리 설명(.Vsdir) 파일
템플릿 디렉터리 설명 파일 (.vsdir)은 IDE (통합 개발 환경)가 대화 상자에서 프로젝트와 연결 된 폴더, 마법사 .vsz 파일 및 템플릿 파일을 표시할 수 있도록 하는 텍스트 파일입니다. 내용에는 파일 또는 폴더 당 하나의 레코드가 포함 됩니다. 여러 폴더, 마법사 또는 템플릿 파일을 설명 하기 위해 일반적으로 하나의 .vsdir 파일만 제공 되지만 참조 된 위치의 모든 .vsdir 파일이 병합 됩니다.

 폴더 (하위 디렉터리), .vsdir 파일에서 참조 되는 파일 및 .vsdir 파일 자체는 모두 동일한 디렉터리에 있습니다. IDE에서 마법사를 실행 하거나 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 폴더 또는 파일을 표시 하는 경우 ide는 실행 된 파일이 들어 있는 디렉터리를 검사 하 여 .vsdir 파일이 있는지 여부를 확인 합니다. .Vsdir 파일이 발견 되 면 IDE에서이 파일을 읽고 실행 된 폴더나 표시 된 폴더 또는 파일에 대 한 항목이 포함 되어 있는지 여부를 확인 합니다. 항목이 발견 되 면 IDE는 마법사 실행 또는 콘텐츠 표시의 정보를 사용 합니다.

 다음 코드 예제는 \<EnvSDK> \bscprj\bscprj\bscprjprojectitems\ Source_Files 레지스트리 키의 SourceFiles. vsdir 파일에서 가져온 것입니다.

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 이 경우 두 레코드가 하나의 파일에 있습니다. 줄 바꿈 문자 (캐리지 리턴 문자)는 각 레코드를 구분 합니다. 각 줄은 다른 파일 형식을 나타냅니다. 파이프 (&#124;) 문자는 각 레코드의 필드를 구분 합니다. 단일 디렉터리에는 파일 이름이 다른 여러 .vsdir 파일이 포함 될 수 있으며, 각 파일 형식에 대해 하나의 .vsdir 파일이 있을 수 있습니다.

## <a name="fields"></a>필드
 다음 표에서는 각 레코드에 대해 지정 된 필드를 나열 합니다.

| 필드 | 설명 |
| - | - |
| 상대 경로 이름 (경로 이름) | 폴더, 템플릿 또는 .vsz 파일의 이름입니다 (예: HeaderFile .h 또는 MyWizard .vsz). 이 필드는 폴더를 나타내는 데 사용 되는 이름일 수도 있습니다. |
| {clsidPackage} | VSPackage의 위성 DLL (동적 연결 라이브러리) 리소스에서 지역화 된 문자열 (예: 프로그램이 localizedname, Description, IconResourceId 및 SuggestedBaseName)에 액세스할 수 있도록 하는 VSPackage의 GUID입니다. IconResourceId는 DLLPath이 제공 되지 않은 경우 적용 됩니다. **참고:**  이전 필드 중 하나 이상이 리소스 식별자가 아니면이 필드는 선택 사항입니다. 일반적으로이 필드는 텍스트를 지역화 하지 않는 타사 마법사에 해당 하는 .vsdir 파일의 경우에는 비어 있습니다. |
| 프로그램이 localizedname | 템플릿 파일 또는 마법사의 지역화 된 이름입니다. 이 필드는 "#ResID" 형식의 문자열 또는 리소스 식별자 일 수 있습니다. 이 이름은 **새 항목 추가** 대화 상자에 표시 됩니다. **참고:**  프로그램이 localizedname가 리소스 식별자 이면 {clsidPackage}가 필요 합니다. |
| SortPriority | 이 템플릿 파일 또는 마법사의 상대적 우선 순위를 나타내는 정수입니다. 예를 들어이 항목의 값이 1 이면이 항목은 값이 1이 고 정렬 값이 2 이상인 모든 항목 앞에 나오는 다른 항목 옆에 표시 됩니다.<br /><br /> 정렬 우선 순위는 동일한 디렉터리의 항목을 기준으로 합니다. 같은 디렉터리에 둘 이상의 .vsdir 파일이 있을 수 있습니다. 이 경우 모든 항목의 항목 <em>입니다.</em> 해당 디렉터리에 있는 vsdir 파일이 병합 됩니다. 우선 순위가 동일한 항목이 표시 되는 이름의 대/소문자를 구분 하지 않는 사전적 순서로 나열 됩니다. `_wcsicmp`함수는 항목의 순서를 정렬 하는 데 사용 됩니다.<br /><br /> .Vsdir 파일에 설명 되지 않은 항목에는 .vsdir 파일에 나열 된 가장 높은 우선 순위 번호 보다 큰 우선 순위 번호가 포함 됩니다. 그 결과 이러한 항목은 이름에 관계 없이 표시 된 목록의 끝에 있습니다. |
| 설명 | 템플릿 파일 또는 마법사에 대 한 지역화 된 설명입니다. 이 필드는 "#ResID" 형식의 문자열 또는 리소스 식별자 일 수 있습니다. 이 문자열은 항목이 선택 될 때 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 나타납니다. |
| DLLPath 또는 {clsidPackage} | 템플릿 파일 또는 마법사의 아이콘을 로드 하는 데 사용 됩니다. 아이콘은 IconResourceId를 사용 하 여 .dll 또는 .exe 파일의 리소스로 로드 됩니다. 이 .dll 또는 .exe 파일은 전체 경로를 사용 하거나 VSPackage GUID를 사용 하 여 식별할 수 있습니다. VSPackage의 구현 DLL은 위성 DLL이 아닌 아이콘을 로드 하는 데 사용 됩니다. |
| IconResourceId | 표시할 아이콘을 결정 하는 DLL 또는 VSPackage 구현 DLL의 리소스 식별자입니다. |
| Flags ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | **새 항목 추가** 대화 상자에서 **이름** 및 **위치** 필드를 사용 하거나 사용 하지 않도록 설정 하는 데 사용 됩니다. **Flags** 필드의 값은 필요한 비트 플래그의 조합에 해당 하는 10 진수입니다.<br /><br /> 사용자가 **새** 탭에서 항목을 선택 하면 프로젝트에서 **새 항목 추가** 대화 상자를 처음 표시할 때 이름 필드와 위치 필드가 표시 되는지 여부를 결정 합니다. Vsdir 파일을 통해 항목을 선택 하면 해당 필드가 활성화 되는지 여부를 제어할 수 있습니다. |
| SuggestedBaseName | 파일, 마법사 또는 템플릿의 기본 이름을 나타냅니다. 이 필드는 "#ResID" 형식의 문자열 또는 리소스 식별자입니다. IDE는이 값을 사용 하 여 항목의 기본 이름을 제공 합니다. MyFile21와 같이 이름을 고유 하 게 만들기 위해이 기준 값에 정수 값이 추가 됩니다.<br /><br /> 위의 목록에서 Description, DLLPath, IconResourceId, Flags 및 SuggestedBaseNumber는 템플릿 및 마법사 파일에만 적용 됩니다. 이러한 필드는 폴더에는 적용 되지 않습니다. 이 사실은 \BscPrj\BscPrj\BscPrjProjectItems 레지스트리 키의 BscPrjProjectItems 파일에 있는 코드에 설명 되어 \<EnvSDK> 있습니다. 이 파일에는 각 레코드에 대 한 4 개의 레코드 (경로 이름, {clsidPackage}, 프로그램이 localizedname 및 SortPriority)가 포함 된 세 개의 레코드 (각 폴더 마다 하나씩)가 포함 되어 있습니다.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 마법사 파일을 만들 때 다음 문제도 고려해 야 합니다.

- 의미 있는 데이터가 없는 모든 필수 필드에는 0이 자리 표시자로 포함 되어야 합니다.

- 지역화 된 이름을 제공 하지 않으면 마법사 파일에 상대 경로 이름이 사용 됩니다.

- DLLPath은 아이콘 위치에 대해 clsidPackage를 재정의 합니다.

- 아이콘을 정의 하지 않으면 IDE는 해당 확장명이 있는 파일의 기본 아이콘을 대체 합니다.

- 제안 된 기본 이름을 제공 하지 않으면 ' Project '가 사용 됩니다.

- .Vsz 파일, 폴더 또는 템플릿 파일을 삭제 하는 경우에는 해당 레코드를 .vsdir 파일 에서도 제거 해야 합니다.

## <a name="see-also"></a>추가 정보
- [마법사로](../../extensibility/internals/wizards.md)
- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
