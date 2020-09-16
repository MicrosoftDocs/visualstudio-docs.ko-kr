---
title: 도메인 특정 언어 도구 UI 개요
description: Visual Studio에서의 도메인 특정 언어 도구 솔루션의 사용자 인터페이스에 대한 개요를 제공합니다.
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 549726d16a5fc1129f8c773ef143267e4c9bc31e
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100724"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>도메인별 언어 도구 사용자 인터페이스 개요
Visual Studio에서 도메인 특정 언어 도구(DSL 도구) 솔루션을 처음으로 열 때 사용자 인터페이스는 다음 그림과 유사합니다.

 ![dsl 디자이너](../modeling/media/dsl_designer.png)

 다음 표에서는 UI의 일부를 사용하는 방법을 설명합니다.

|**요소**|**정의**|
|-|-|
|다이어그램|다이어그램에는 도메인 모델이 표시됩니다.<br /><br /> 다이어그램에는 두 가지 측면이 있습니다. 한 측면에서는 모델의 요소 형식을 정의합니다. 다른 측면에서는 화면에 모델이 표시되는 방식을 정의합니다.|
|도구 상자|도구 상자에서 도구를 끌어서 다이어그램에 도메인 클래스 및 도형 유형을 추가할 수 있습니다. 관계, 커넥터 및 도형 맵을 추가하려면 도구를 클릭하고 다이어그램에서 소스 노드를 선택한 다음, 대상 노드를 클릭합니다.|
|DSL 탐색기|DSL 정의가 활성 창일 경우 **DSL 탐색기**가 표시됩니다. 여기에는 DSL이 트리로 표시됩니다. DSL 탐색기를 사용하면 다이어그램에 표시되지 않는 모델의 기능을 편집할 수 있습니다. 예를 들어 **DSL 탐색기**를 사용하여 도구 상자 항목을 추가하고 유효성 검사 프로세스를 사용하도록 설정할 수 있습니다.|
|DSL 정보 창|**DSL 정보** 창에는 요소가 표시되는 방식과 요소가 복사 및 삭제되는 방식을 제어하는 데 사용할 수 있는 도메인 모델의 요소 속성이 표시됩니다.<br /><br /> -   기본적으로 **DSL 정보** 창은 **오류 목록** 및 **출력** 창 옆에 표시됩니다.|

## <a name="the-domain-model-diagram"></a>도메인 모델 다이어그램
 도메인 모델 다이어그램은 두 부분으로 나뉩니다. 다이어그램의 한 측면에는 모델의 요소 및 관계가 표시됩니다. 다른 측면에는 모델이 표시되는 방식이 표시되며, 모델 다이어그램의 속성 및 요소를 표시하는 데 사용되는 도형이 포함됩니다. 다음 그림에서는 다이어그램의 요소를 보여 줍니다.

 ![스윔 레인이 있는 dsl 디자이너](../modeling/media/dsl_desinger.png)

 다음 표에서는 도메인 모델 다이어그램의 일부 요소를 설명합니다.

|**기간**|**정의**|
|-|-|
|도메인 클래스|도메인 클래스는 모델의 요소 형식입니다.<br /><br /> 도메인 클래스는 둘 이상 관계의 대상일 경우 다이어그램에 두 번 이상 나타날 수 있습니다.<br /><br /> 도메인 클래스를 추가하려면 **도구 상자**에서 다이어그램의 **클래스 및 관계** 측면으로 도메인 클래스 도구를 끕니다.|
|도메인 관계|도메인 관계는 모델에서 요소 간의 링크 형식입니다.<br /><br /> *포함 관계*는 소스 요소가 대상 요소를 소유하거나 포함하고 있음을 나타내며 실선으로 표시됩니다. 모델의 모든 요소는 모델이 트리를 형성할 수 있도록 포함 관계 하나의 대상이어야 합니다. *참조 관계*는 모델 요소 간의 일반적인 링크를 나타내며 점선으로 표시됩니다. 모든 요소에는 참조 링크가 얼마든지 포함될 수 있습니다.<br /><br /> **도구 상자**에서 도구를 클릭하고 소스 도메인 클래스를 클릭한 후 대상 클래스를 클릭하여 관계를 만들 수 있습니다.|
|모양 및 연결선|도형은 DSL 다이어그램에 모델 요소가 표시되는 방식을 지정하고, 커넥터는 관계를 표시하는 데 사용될 수 있는 DSL 다이어그램의 선을 지정합니다.<br /><br /> 도형이나 커넥터를 만들려면 다이어그램의 **다이어그램 요소** 측면으로 도구를 끕니다.|
|모양 맵|도형 맵은 도메인 모델 다이어그램에 선으로 표시되며, 도형을 관련 도메인 클래스에 연결하거나 커넥터를 관련 도메인 관계에 연결합니다.|

## <a name="see-also"></a>추가 정보

- [도메인별 언어 도구 개요](../modeling/overview-of-domain-specific-language-tools.md)
- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)
