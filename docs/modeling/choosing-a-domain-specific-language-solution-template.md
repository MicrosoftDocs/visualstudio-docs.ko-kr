---
title: 도메인별 언어 솔루션 템플릿 선택
description: Domain-Specific 언어 디자이너 마법사에서 사용할 수 있는 솔루션 템플릿 중 하나를 선택하여 도메인별 언어 솔루션을 만드는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1c638c5a45427fd474f085ff58c9d38682ee054
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385437"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>도메인별 언어 솔루션 템플릿 선택
도메인별 언어 솔루션을 만들려면 Domain-Specific 언어 디자이너 마법사에서 사용할 수 있는 솔루션 템플릿 중 하나를 선택합니다. 만들려는 언어와 가장 유사한 템플릿을 선택하면 시작 솔루션에 대해 수정해야 하는 사항을 최소화할 수 있습니다.

 다음 솔루션 템플릿은 Domain-Specific 언어 디자이너 마법사에서 사용할 수 있습니다.

|템플릿|기능|설명|
|-|-|-|
|클래스 다이어그램|- 구획 모양<br />- 클래스 상속<br />- 관계 상속<br />- 셰이프 상속<br />- 관계 속성|도메인별 언어에 속성이 있는 엔터티 및 관계가 포함된 경우 이 솔루션 템플릿을 사용합니다. 이 템플릿은 UML 클래스 다이어그램과 유사한 도메인별 언어를 만듭니다. 기본 엔터티는 연결, 일반화 및 구현 관계와 함께 클래스 및 인터페이스입니다. 클래스 또는 인터페이스는 특성 목록을 포함하는 상자로 나타납니다.|
|구성 요소 다이어그램|- 포트|도메인별 언어에 구성 요소, 즉 소프트웨어 시스템의 일부가 포함된 경우 이 솔루션 템플릿을 사용합니다. 이 템플릿은 UML 구성 요소 다이어그램과 유사한 도메인별 언어를 만듭니다. 기본 엔터티는 구성 요소 및 포트이며 구성 요소 외부에 작은 모양으로 표시됩니다.|
|작업 흐름 다이어그램|- 이미지 및 기하 도형<br />-   *스윔 레인*|도메인별 언어에 워크플로, 상태 또는 시퀀스가 포함된 경우 이 솔루션 템플릿을 사용합니다. 이 템플릿은 UML 작업 다이어그램과 유사한 도메인별 언어를 만듭니다. 주 엔터티는 활동이며 주 관계는 활동 간의 전환입니다. 템플릿에는 시작 상태, 최종 상태 및 동기화 막대와 같은 몇 가지 다른 요소가 포함되어 있습니다.|
|최소 언어|- 클래스 및 셰이프 1개<br />- 하나의 관계 및 커넥터|도메인별 언어가 다른 템플릿과 유사하지 않은 경우 이 솔루션 템플릿을 사용합니다. 이 템플릿은 **도구 상자에** **Box** 및 **Line** 으로 표시되는 두 개의 클래스와 하나의 관계가 있는 도메인별 언어를 만듭니다. 클래스와 관계에는 각각 예제 문자열 속성이 있습니다.|
|최소 WinForm 디자이너|- 작은 모델입니다.<br />- 모델을 표시하는 Windows Form입니다.|DSL이 그래픽 디자이너가 아닌 Windows Form에 바인딩된 애플리케이션을 빌드하려면 이 템플릿을 사용합니다.<br /><br /> 언어의 사용자 인터페이스 역할을 하는 양식은 Dsl\UI 폴더에 있습니다.<br /><br /> 양식 디자이너를 열기 전에 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [Windows Forms-Based Domain-Specific 언어 만들기를 참조하세요.](../modeling/creating-a-windows-forms-based-domain-specific-language.md)|
|최소 WPF 디자이너|- 작은 모델<br />- 모델을 표시하는 Windows Presentation Foundation 사용자 인터페이스|DSL이 그래픽 디자이너가 아닌 WPF 사용자 인터페이스에 바인딩된 애플리케이션을 빌드하려면 이 템플릿을 사용합니다.<br /><br /> 사용자 인터페이스의 디자이너는 Dsl\UI 폴더에 있습니다.<br /><br /> UI 디자이너를 열기 전에 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [WPF-Based Domain-Specific 언어 만들기를 참조하세요.](../modeling/creating-a-wpf-based-domain-specific-language.md)|
|DSL 라이브러리|- 최소 라이브러리|다른 DSL 정의로 가져올 수 있는 부분 DSL 정의를 빌드하려면 이 템플릿을 사용합니다.|

## <a name="see-also"></a>추가 정보

- [도메인별 언어 도구 개요](../modeling/overview-of-domain-specific-language-tools.md)
