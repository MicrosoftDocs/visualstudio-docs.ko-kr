---
title: R 코드 Lint
description: Linter 옵션을 포함하여 R에 대한 Visual Studio의 기본 제공 Lint 지원을 사용하는 방법입니다.
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: aecf9d95fb8a3b2cda659e2694bff145424e150b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970742"
---
# <a name="lint-r-code-in-visual-studio"></a>Visual Studio에서 R 코드 Lint

Linter는 잠재적 오류, 서식 지정 문제 및 기타 코드 노이즈(예: 잘못된 공백)를 표시하기 위해 코드를 분석합니다. 또한 Linter는 식별자의 이름 지정 방법과 같은 특정 코딩 규칙을 권장하는 데에도 도움이 됩니다. 이러한 규칙은 팀 및 기타 공동 작업 상황에서 유용합니다.

RTVS(Visual Studio용 R 도구)는 R에 대해 이 문서에 설명된 다양한 옵션을 통해 동작을 제어하는 기본 제공 Linter를 제공합니다. 이러한 옵션은 **도구** > **옵션** > **텍스트 편집기** > **R** > **Lint**에 있습니다.

Lint는 기본적으로 비활성화되어 있습니다. Lint를 사용하도록 설정하려면 **전체** > **Lint 사용** 옵션을 **True**로 설정합니다.

사용하도록 설정하면 입력 중에 Linter가 편집기에서 실행됩니다. 문제는 녹색 오류 표시선으로 표시됩니다. 예를 들어 다음 그래픽에서 RTVS는 할당에 `=` 대신 `<-` 사용, 함수 인수 앞뒤 공백 문제, 파스칼식 대/소문자 및 대문자 식별자 사용 및 세미콜론 사용을 비롯한 여섯 가지 Lint 문제를 식별합니다. 문제에 커서를 올리면 설명을 표시합니다.

![R 코드에 대한 Linter 출력의 예](media/linting-01.png)

프로젝트 또는 파일의 필요에 따라 Linter 옵션을 변경할 수 있습니다. 예를 들어 온라인 과정의 샘플 코드는 파스칼식 대/소문자 식별자와 함께 `=` 대신 `<-`를 사용할 수 있습니다. 기본 Linter 옵션은 이러한 경우에 플래그를 지정하므로 해당 코드는 빈번한 Linter 경고를 표시합니다. 해당 코드로 작업하는 동안 각 인스턴스를 수정하는 데 시간을 보내는 대신 옵션을 사용하지 않도록 설정할 수 있습니다.

## <a name="assignment-group"></a>할당 그룹

| 옵션 | 기본값 | Lint 효과 |
| --- | --- | --- |
| **Enforce \<-** | **True** | `<-`를 할당에 사용하지 않는 경우를 식별합니다. |

## <a name="naming-group"></a>그룹 이름 지정

이러한 옵션은 다른 명명 규칙을 사용하는 식별자의 플래그를 지정합니다.

| 옵션 | 기본값 | Lint 효과 |
| --- | --- | --- |
| **camelCase에 플래그 지정** | **False** | camelCase를 사용하는 식별자에 플래그를 지정합니다. |
| **긴 이름에 플래그 지정** | **False** | **최대 이름 길이** 설정을 초과하도록 명명된 식별자에 플래그를 지정합니다. |
| **여러 점에 플래그 지정** | **True** | 여러 개의 점을 사용하는 식별자에 플래그를 지정합니다. |
| **PascalCase에 플래그 지정** | **True** | PascalCase를 사용하는 식별자에 플래그를 지정합니다. |
| **snake_case에 플래그 지정** | **False** | 믿줄을 사용하는 식별자에 플래그를 지정합니다. |
| **UPPERCASE에 플래그 지정** | **True** | 모든 대문자를 사용하는 식별자에 플래그를 지정합니다. |
| **최대 이름 길이** | **32** | **긴 이름에 플래그 지정** 설정을 적용하는 길이입니다. |

## <a name="spacing-group"></a>그룹 간격 지정

기본적으로 모두 **True**로 설정된 이러한 옵션은 Linter에서 공백 문제를 식별하는 위치를 제어합니다(예: 함수 이름 뒤, 콤마 앞뒤, 여는 중괄호 위치와 닫는 중괄호 위치, ( 앞 공백 및 () 내 공백).

## <a name="statements-group"></a>문 그룹

| 옵션 | 기본값 | Lint 효과 |
| --- | --- | --- |
| **여러 항목** | **True** | 같은 줄에 여러 문이 있는 경우를 식별합니다. |
| **세미콜론** | **True** | 세미콜론의 용도를 식별합니다. |

## <a name="text-group"></a>텍스트 그룹

| 옵션 | 기본값 | Lint 효과 |
| --- | --- | --- |
| **줄 길이 제한** | **False** | Linter가 **최대 줄 길이** 옵션보다 긴 줄에 플래그를 지정하는지를 설정합니다. |
| **최대 줄 길이** | **80** | **줄 길이 제한** 옵션을 적용한 줄 길이를 설정합니다. |

## <a name="whitespace-group"></a>공백 그룹

기본적으로 모두 **True**로 설정된 이러한 옵션은 Linter에서 공백 문제를 식별하는 위치를 제어합니다(예: 탭 사용, 큰따옴표 사용, 후행 빈 줄 및 후행 공백).