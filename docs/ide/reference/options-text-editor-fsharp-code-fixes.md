---
title: 옵션, 텍스트 편집기, F#, 코드 수정
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c20646c8da4101ac674a64c5ca1ed23a3b1fd7b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770930"
---
# <a name="options-text-editor--f--code-fixes"></a>옵션: 텍스트 편집기 > F# > 코드 수정

코드 수정 옵션 페이지를 사용하여 코드 오류를 식별하고 해결 방법을 제공하는 데 도움이 될 수 있는 설정을 지정합니다. 이 옵션 페이지에 액세스하려면 **도구** > **옵션**을 선택한 다음, **텍스트 편집기** > **F#**  > **코드 수정**을 선택합니다.

## <a name="code-fixes"></a>코드 수정

- **이름 단순화(불필요한 한정자 제거)**

  이 확인란을 선택하면 자주 사용되는 네임스페이스의 멤버와 같이 한정자가 필요하지 않은 경우 정규화된 이름이 단순화됩니다.

- **항상 최상위에 open 문 배치**

  이 확인란을 선택하고 코드에 `open` 문을 입력하면 해당 문이 최상위에 배치됩니다.

- **사용되지 않는 open 문 제거**

  이 확인란을 선택하면 사용하지 않은 `open` 문에 대해 문서가 분석되고, 사용하지 않은 모든 `open` 문을 제거하는 작업이 [빠른 작업](../quick-actions.md) 전구 아이콘과 함께 표시됩니다.

- **사용되지 않는 값에 대해 수정 사항 분석 및 제안**

  이 확인란을 선택하면 도구가 코드에서 사용되지 않는 값을 인식합니다. 그런 다음, 사용되지 않는 값을 가리키면 값을 사용할 수 있는 추천 방법이 표시됩니다.

## <a name="see-also"></a>참조

- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
- [CodeLens에서 코드 변경 내용 및 기타 기록 찾기](../../ide/find-code-changes-and-other-history-with-codelens.md)
