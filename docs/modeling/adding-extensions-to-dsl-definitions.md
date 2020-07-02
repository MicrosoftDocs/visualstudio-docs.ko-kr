---
title: DSL 정의에 확장 추가
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2500fc8d9e09d95d7972a4b151b01937a5570a08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544237"
---
# <a name="add-extensions-to-dsl-definitions"></a>DSL 정의에 확장 추가

DSL 정의 확장을 사용 하면 DSL (도메인별 언어)에 대 한 확장 패키지를 만들 수 있습니다. VSIX (Visual Studio Integration Extension)에 포함 된 DSL 확장은 DSL과 동일한 방식으로 사용자의 컴퓨터에 설치할 수 있습니다. 추가 기능은 런타임에 동적으로 사용 하도록 설정 하 고 비활성화할 수 있습니다. Dsl은 확장을 위해 명시적으로 설계 하지 않아도 되며 확장 된 DSL을 변경 하지 않고 나중에 또는 제 3 자가 확장을 디자인할 수 있습니다.

DSL 확장에는 다음과 같은 기능이 포함 될 수 있습니다.

- 모델 및 프레젠테이션 요소의 속성

- 데코레이터 셰이프 및 연결선

- 클래스, 관계, 모양 및 연결선

- 유효성 검사 제약 조건

- 도구 상자 항목 및 탭

확장 된 DSL의 사용자는 추가 기능의 인스턴스를 포함 하는 모델을 만들고 저장할 수 있습니다. 적절 한 확장을 설치한 다른 사용자가 모델을 읽을 수 있습니다. 확장을 설치 하지 않은 사용자는 추가 기능을 사용할 수 없지만 추가 기능을 잃지 않고도 모델을 업데이트 하 고 저장할 수 있습니다.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>참고 항목

- [관련 블로그 게시물](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
