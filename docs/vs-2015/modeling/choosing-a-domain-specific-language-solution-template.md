---
title: 도메인별 언어 솔루션 템플릿 선택 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6522e3a1ad10f221f0ed7fc1761559ee9bc3f9b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668346"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>도메인별 언어 솔루션 템플릿 선택
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도메인별 언어 솔루션을 만들려면 도메인 특정 언어 디자이너 마법사에서 사용할 수 있는 솔루션 템플릿 중 하나를 선택 합니다. 만들려는 언어와 가장 비슷한 템플릿을 선택 하면 시작 솔루션에 대 한 수정 사항을 최소화할 수 있습니다.

 다음 솔루션 템플릿은 도메인 특정 언어 디자이너 마법사에서 사용할 수 있습니다.

> [!NOTE]
> 템플릿의 목적은 시작 DSL을 제공 하는 것입니다. 클래스 및 구성 요소 다이어그램 이라는 템플릿은 전체 UML 다이어그램이 아닙니다. UML 모델을 만들려면 단일 모델 주위에 통합 된 다이어그램 집합을 제공 하는 UML 모델링 도구를 고려해 보세요. ModelBus를 사용하면 이러한 다이어그램을 확장할 수 있으며 DSL과 통합할 수 있습니다. 자세한 내용은 [앱에 대 한 모델 만들기](../modeling/create-models-for-your-app.md)를 참조 하세요.

|템플릿|기능|설명|
|--------------|--------------|-----------------|
|클래스 다이어그램|-구획 도형<br />-클래스 상속<br />-관계 상속<br />-모양 상속<br />-관계 속성|도메인 특정 언어에 속성이 있는 엔터티 및 관계가 포함 된 경우이 솔루션 템플릿을 사용 합니다. 이 템플릿은 UML 클래스 다이어그램과 유사한 도메인별 언어를 만듭니다. 기본 엔터티는 연결, 일반화 및 구현 관계와 함께 클래스 및 인터페이스입니다. 클래스 또는 인터페이스가 특성 목록을 포함 하는 상자로 나타납니다.|
|구성 요소 다이어그램|-포트|도메인 특정 언어에 구성 요소 (소프트웨어 시스템의 구성 요소)가 포함 된 경우이 솔루션 템플릿을 사용 합니다. 이 템플릿은 UML 구성 요소 다이어그램과 유사한 도메인별 언어를 만듭니다. 주요 엔터티는 구성 요소 외부에 작은 모양으로 표시 되는 구성 요소 및 포트입니다.|
|작업 흐름 다이어그램|-이미지 및 기 하 도형 모양<br />-   *스윔 레인*|도메인 특정 언어에 워크플로, 상태 또는 시퀀스가 포함 되어 있는 경우이 솔루션 템플릿을 사용 합니다. 이 템플릿은 UML 동작 다이어그램과 유사한 도메인별 언어를 만듭니다. 주 엔터티는 활동 이며 주 관계는 활동 간을 전환 하는 것입니다. 템플릿에는 시작 상태, 최종 상태 및 동기화 표시줄과 같은 몇 가지 다른 요소가 포함 되어 있습니다.|
|최소 언어|-One 클래스 및 모양<br />-관계 및 연결선 하나|도메인별 언어가 다른 템플릿과 유사 하지 않을 경우이 솔루션 템플릿을 사용 합니다. 이 템플릿은 **도구 상자** 에 **상자** 와 **선**으로 표시 되는 두 개의 클래스와 하나의 관계가 있는 도메인별 언어를 만듭니다. 클래스와 관계에는 각각 예제 문자열 속성이 있습니다.|
|최소 WinForm 디자이너|-작은 모델입니다.<br />-모델을 표시 하는 Windows Form입니다.|DSL이 그래픽 디자이너가 아닌 Windows Form에 바인딩되는 응용 프로그램을 빌드 하려는 경우이 템플릿을 사용 합니다.<br /><br /> 언어에 대 한 사용자 인터페이스 역할을 하는 양식은 Dsl\UI. 폴더에 있습니다.<br /><br /> 폼 디자이너를 열려면 먼저 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [Windows Forms 기반 도메인별 언어 만들기](../modeling/creating-a-windows-forms-based-domain-specific-language.md)를 참조 하세요.|
|최소 WPF 디자이너|-작은 모델<br />-모델을 표시 하는 Windows Presentation Foundation 사용자 인터페이스|DSL이 그래픽 디자이너가 아닌 WPF 사용자 인터페이스에 바인딩되는 응용 프로그램을 빌드 하려는 경우이 템플릿을 사용 합니다.<br /><br /> 사용자 인터페이스의 디자이너는 Dsl\UI. 폴더에 있습니다.<br /><br /> UI 디자이너를 열려면 먼저 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [WPF 기반 도메인별 언어 만들기](../modeling/creating-a-wpf-based-domain-specific-language.md)를 참조 하세요.|
|DSL 라이브러리|-최소 라이브러리|다른 DSL 정의로 가져올 수 있는 부분 DSL 정의를 작성 하려는 경우이 템플릿을 사용 합니다.|

## <a name="see-also"></a>관련 항목
 [도메인별 언어 도구 개요](../modeling/overview-of-domain-specific-language-tools.md)
