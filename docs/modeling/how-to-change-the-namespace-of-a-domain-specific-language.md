---
title: '방법: 도메인별 언어의 네임 스페이스 변경'
ms.date: 10/31/2018
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, namespace
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ff7c73694cb53f7fbea21514feeaab4abce3f29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542677"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>방법: 도메인별 언어의 네임 스페이스 변경

도메인 특정 언어의 네임 스페이스를 변경할 수 있습니다. Dsl **탐색기**, dsl 패키지 프로젝트의 속성 및 어셈블리 정보에서 변경을 수행 합니다.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>도메인별 언어의 네임 스페이스를 변경 하려면

1. **Dsl 탐색기**에서 **dsl** 노드를 선택 합니다.

2. **속성** 창에서 **Namespace** 속성을 변경 합니다.

3. 솔루션을 저장 하 고 템플릿을 변환 합니다.

4. **프로젝트** 메뉴에서 **Dsl 속성**을 선택 합니다.

   프로젝트의 속성이 표시 됩니다.

5. **응용 프로그램** 탭을 선택 합니다.

6. **기본 네임 스페이스** 속성을 새 네임 스페이스 이름으로 변경 합니다.

7. 또한 어셈블리 이름을 변경 하려면 **어셈블리 이름 속성을 변경 합니다.**

8. 어셈블리 이름을 변경한 경우 DslPackage\Package.tt를 열고 다음 줄을 업데이트 합니다.

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. 사용자 지정 코드를 작성 한 경우에는 코드 파일에서 네임 스페이스와 클래스 참조를 변경 해야 합니다.

10. Visual Studio 실험적 인스턴스를 다시 설정 합니다.

    1. ** \\ \Users**_{your name}_**\AppData\Local\Microsoft\VisualStudio \\ \* Exp**를 삭제 합니다.

    2. Windows **시작** 메뉴에서 **모든 프로그램**  >  **Microsoft Visual Studio 2010 SDK**Tools를 선택 하  >  **Tools**  >  **여 실험적 인스턴스를 다시 설정**합니다.

11. **빌드** 메뉴에서 **솔루션 다시 빌드**를 선택 합니다.

## <a name="see-also"></a>참고 항목

[도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)