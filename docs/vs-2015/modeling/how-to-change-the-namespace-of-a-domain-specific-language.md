---
title: '방법: 도메인별 언어의 네임 스페이스 변경 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671730"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>방법: 도메인별 언어의 네임스페이스 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도메인 특정 언어의 네임 스페이스를 변경할 수 있습니다. Dsl **탐색기**에서 dsl 패키지 프로젝트의 속성 및 어셈블리 정보를 변경 해야 합니다.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>도메인별 언어의 네임 스페이스를 변경 하려면

1. **Dsl 탐색기**에서 **dsl** 노드를 클릭 합니다.

2. **속성** 창에서 **Namespace** 속성을 변경 합니다.

3. 솔루션을 저장 하 고 템플릿을 변환 합니다.

4. **프로젝트** 메뉴에서 **Dsl 속성**을 클릭 합니다.

     프로젝트의 속성이 표시 됩니다.

5. **애플리케이션** 탭을 클릭합니다.

6. **기본 네임 스페이스** 속성을 새 네임 스페이스 이름으로 변경 합니다.

7. 또한 어셈블리 이름을 변경 하려면 **어셈블리 이름 속성을 변경 합니다.**

8. 어셈블리 이름을 변경한 경우 DslPackage\Package.tt를 열고 다음 줄을 업데이트 합니다.

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. 사용자 지정 코드를 작성 한 경우에는 코드 파일에서 네임 스페이스와 클래스 참조를 변경 해야 합니다.

10. Visual Studio 실험적 인스턴스를 다시 설정 합니다.

    1. ** \\ \Users**_{your name}_**\AppData\Local\Microsoft\VisualStudio \\ \* Exp** 삭제

    2. Windows **시작** 메뉴에서 **모든 프로그램**, **Microsoft Visual Studio 2010 SDK**, **도구**, **실험적 인스턴스 다시 설정**을 차례로 선택 합니다.

11. **빌드** 메뉴에서 **솔루션 다시 빌드**를 선택 합니다.

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
