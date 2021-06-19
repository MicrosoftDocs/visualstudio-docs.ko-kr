---
title: 도메인별 언어 사용자 지정 및 확장
description: Visual Studio 모델링 및 시각화 SDK(VMSDK)에서 모델링 도구를 정의할 수 있는 몇 가지 수준을 제공하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04180b1fc8930b58c2d78635c794c8a614db5ed5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389386"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>도메인별 언어 사용자 지정 및 확장

Visual Studio 모델링 및 시각화 SDK(VMSDK)는 모델링 도구를 정의할 수 있는 몇 가지 수준을 제공합니다.

1. DSL 정의 다이어그램을 사용하여 DSL(도메인 특정 언어)을 정의합니다. 다이어그램 표기법, 읽을 수 있는 XML 양식 및 코드 및 기타 아티팩트 생성에 필요한 기본 도구를 사용하여 DSL을 빠르게 만들 수 있습니다. 자세한 내용은 [Domain-Specific 언어를 정의하는 방법을 참조하세요.](../modeling/how-to-define-a-domain-specific-language.md)

2. DSL 정의의 고급 기능을 사용하여 DSL을 미세 조정합니다. 예를 들어 사용자가 요소를 만들 때 추가 링크를 표시할 수 있습니다. 이러한 기술은 대부분 DSL 정의에서 달성되며, 일부 기술에는 몇 줄의 프로그램 코드가 필요합니다.

3. 프로그램 코드를 사용하여 모델링 도구를 확장합니다. VMSDK는 DSL 정의에서 생성된 코드를 사용하여 확장을 쉽게 통합할 수 있도록 설계되었습니다. 자세한 내용은 [Domain-Specific 언어를 사용자 지정하는 코드 작성을 참조하세요.](../modeling/writing-code-to-customise-a-domain-specific-language.md)

> [!NOTE]
> DSL 정의 파일을 업데이트한 경우 솔루션을 다시 빌드하기 전에 **솔루션 탐색기** 도구 모음에서 **모든 템플릿 변환을** 클릭해야 합니다.

## <a name="article-reference"></a>문서 참조

|이 효과를 얻으려면|이 항목을 참조하세요.|
|-|-|
|사용자가 도형의 색 및 스타일 속성을 설정할 수 있도록 허용합니다.|셰이프 또는 커넥터 클래스를 마우스 오른쪽 단추로 클릭하고 **노출된 추가를** 가리킨 다음 항목을 클릭합니다.|
|모델 요소의 여러 클래스는 다이어그램에서 비슷하게 표시되며 초기 높이 및 너비, 색, 도구 설명과 같은 속성을 공유합니다.|셰이프 또는 커넥터 클래스 간에 상속을 사용합니다. 파생된 도형과 파생된 도메인 클래스 간의 매핑은 부모의 매핑 세부 정보를 상속합니다.<br /><br /> 또는 다른 도메인 클래스를 동일한 셰이프 클래스에 매핑합니다.|
|모델 요소의 클래스는 다양한 도형 컨텍스트에 의해 표시됩니다.|두 개 이상의 셰이프 클래스를 동일한 도메인 클래스에 매핑합니다. 솔루션을 빌드할 때 오류 보고서에 따라 요청된 코드를 제공하여 사용할 모양을 결정합니다.|
|모양 색 또는 글꼴과 같은 기타 기능은 현재 상태를 나타냅니다.|[모델을 반영하도록 도형 및 커넥터 업데이트를](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)참조하세요.<br /><br /> 노출된 속성을 업데이트하는 규칙을 만듭니다. [규칙 모델 내의 변경 내용 전파를](../modeling/rules-propagate-changes-within-the-model.md)참조하세요.<br /><br /> 또는 OnAssociatedPropertyChanged()를 사용하여 링크 화살표 또는 글꼴과 같은 노출되지 않는 기능을 업데이트합니다.|
|셰이프의 아이콘이 상태를 나타내기 위해 변경되었습니다.|DSL 세부 정보 창에서 데코레이터 매핑의 표시 여부 설정 동일한 위치에서 여러 이미지 데코레이터를 찾습니다. [모델을 반영하도록 도형 및 커넥터 업데이트를](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)참조하세요.<br /><br /> 또는 를 `ImageField.GetDisplayImage()` 재정의합니다. 의 예제를 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> 참조하세요.|
|모든 셰이프에 배경 이미지 설정|InitializeInstanceResources()를 재정의하여 고정된 ImageField를 추가합니다.|
|도형을 깊이에 중첩|재귀 포함 트리를 설정합니다. 셰이프를 포함하도록 BoundsRules를 정의합니다.|
|요소 경계의 고정 지점에 커넥터를 연결합니다.|다이어그램의 작은 포트로 표현되는 포함된 터미널 요소를 정의합니다. BoundsRules를 사용하여 현재 위치의 포트를 수정합니다. 시각화 및 모델링 [SDK에서](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)회로 다이어그램 샘플을 참조하세요.|
|텍스트 필드에는 다른 값에서 파생된 값이 표시됩니다.|텍스트 데코레이터를 계산 또는 사용자 지정 스토리지 도메인 속성에 매핑합니다. 자세한 내용은 계산 및 사용자 지정 스토리지 속성 을 [참조하세요.](../modeling/calculated-and-custom-storage-properties.md)|
|모델 요소 간 또는 도형 간에 변경 내용 전파|[Domain-Specific 언어의 유효성 검사를](../modeling/validation-in-a-domain-specific-language.md)참조하세요.|
|저장소 외부의 다른 Visual Studio 확장과 같은 리소스에 변경 내용을 전파합니다.|[이벤트 처리기 모델 외부의 변경 내용 전파를](../modeling/event-handlers-propagate-changes-outside-the-model.md)참조하세요.|
|속성 창에는 관련 요소의 속성이 표시됩니다.|속성 전달을 설정합니다. [속성 창 사용자 지정을](../modeling/customizing-the-properties-window.md)참조하세요.|
|속성 범주|속성 창은 범주라는 섹션으로 나뉩니다. 도메인 속성의 **범주를** 설정합니다. 범주 이름이 같은 속성이 동일한 섹션에 표시됩니다. 관계 역할의 **범주를** 설정할 수도 있습니다.|
|도메인 속성에 대한 사용자 액세스 제어|도메인 **속성이** 런타임에 속성 창 나타나지 않도록 하려면 검색 가능 false로 설정합니다. 텍스트 데코레이터에 매핑할 수 있습니다.<br /><br /> **UI 읽기 전용인 경우** 사용자가 도메인 속성을 변경할 수 없습니다.<br /><br /> 도메인 속성에 대한 프로그램 액세스는 영향을 받지 않습니다.|
|DSL의 모델 탐색기에서 노드의 이름, 아이콘 및 표시 유형 변경|[모델 탐색기 사용자 지정을](../modeling/customizing-the-model-explorer.md)참조하세요.|
|복사, 잘라내기 및 붙여넣기 사용|DSL 탐색기에서 **편집기** 노드의 **붙여넣기 복사 사용** 속성을 설정합니다.|
|요소를 복사할 때마다 참조 링크 및 해당 대상을 복사합니다. 예를 들어 항목에 첨부된 주석을 복사합니다.|원본 역할의 **Propagates Copy** 속성을 설정합니다(DSL 정의 다이어그램에서 도메인 관계의 한 쪽에 있는 줄로 표시).<br /><br /> 더 복잡한 효과를 얻기 위해 ProcessOnCopy를 재정의하는 코드를 작성합니다.<br /><br /> [복사 동작 사용자 지정을](../modeling/customizing-copy-behavior.md)참조하세요.|
|요소를 삭제할 때 관련 요소를 삭제, 다시 부모 또는 다시 연결합니다.|관계 역할의 **전파 삭제** 값을 설정합니다. 더 복잡한 효과의 경우 `ShouldVisitRelationship` `ShouldVisitRolePlayer` `MyDslDeleteClosure` **DomainModel.cs** 에 정의된 클래스의 및 메서드를 재정의합니다.|
|복사 및 끌어서 놓기에서 모양 레이아웃과 모양을 유지합니다.|셰이프 및 커넥터를 복사된 에 `ElementGroupPrototype` 추가합니다. 재정의하는 가장 편리한 방법은 입니다. `ElementOperations.CreateElementGroupPrototype()`<br /><br /> [복사 동작 사용자 지정을](../modeling/customizing-copy-behavior.md)참조하세요.|
|선택한 위치(예: 현재 커서 위치)에 모양을 붙여넣습니다.|위치별 버전의 를 사용하도록 를 `ClipboardCommandSet.ProcessOnCopy()` `ElementOperations.Merge().` [재정의합니다. 복사 동작 사용자 지정을 참조하세요.](../modeling/customizing-copy-behavior.md)|
|붙여넣을 때 추가 링크 만들기|ClipboardCommandSet.ProcessOnPasteCommand() 재정의|
|이 다이어그램, 다른 DSL 및 Windows 요소에서 끌어서 놓기 사용|[방법: 끌어서 놓기 처리기 추가를](../modeling/how-to-add-a-drag-and-drop-handler.md) 참조하세요.|
|부모로 끌어온 것처럼 도형 또는 도구를 포트와 같은 자식 모양으로 끌 수 있습니다.|대상 개체 클래스에서 요소 병합 지시문을 정의하여 삭제된 개체를 부모로 전달합니다. [요소 만들기 및 이동 사용자 지정을](../modeling/customizing-element-creation-and-movement.md)참조하세요.|
|도형 또는 도구를 도형으로 끌어서 추가 링크 또는 개체를 만들 수 있습니다. 예를 들어 주석을 연결할 항목에 놓을 수 있도록 합니다.|대상 도메인 클래스에서 요소 병합 지시문을 정의하고 생성할 링크를 정의합니다. 복잡한 경우 사용자 지정 코드를 추가할 수 있습니다. [요소 만들기 및 이동 사용자 지정을](../modeling/customizing-element-creation-and-movement.md)참조하세요.|
|하나의 도구를 사용하여 요소 그룹을 만듭니다. 예를 들어 고정 포트 집합이 있는 구성 요소입니다.|ToolboxHelper.cs에서 도구 상자 초기화 메서드를 재정의합니다. 요소와 해당 관계 링크를 포함하는 EGP(요소 그룹 프로토타입)를 만듭니다. [도구 및 도구 상자 사용자 지정을](../modeling/customizing-tools-and-the-toolbox.md)참조 하세요.<br /><br /> 가 중에 주 및 포트 셰이프를 포함 하거나, Boundsrules로를 정의 하 여가 중 p가 인스턴스화될 때 포트 셰이프를 배치 합니다.|
|하나의 연결 도구를 사용 하 여 여러 유형의 관계를 인스턴스화합니다.|도구에서 호출 하는 연결 작성기에 LCD (링크 연결 지시문)를 추가 합니다. Lcd는 두 요소의 형식에서 관계의 형식을 결정 합니다. 요소의 상태에 따라 달라 지도록 사용자 지정 코드를 추가할 수 있습니다. [도구 및 도구 상자 사용자 지정을](../modeling/customizing-tools-and-the-toolbox.md)참조 하세요.|
|스티커 도구-사용자는 도구를 두 번 클릭 하 여 여러 셰이프 또는 연결선을 연속 해 서 만들 수 있습니다.|DSL 탐색기에서 노드를 선택 `Editor` 합니다. 속성 창에서는 **고정 도구 상자 항목을 사용** 합니다.|
|메뉴 명령 정의|[방법: 표준 메뉴 명령 수정을](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md) 참조 하세요.|
|유효성 검사 규칙을 사용 하 여 모델 제약|[Domain-Specific 언어로 유효성 검사를](../modeling/validation-in-a-domain-specific-language.md) 참조 하세요.|
|DSL에서 코드, 구성 파일 또는 문서를 생성 합니다.|[도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)|
|모델을 파일에 저장 하는 방법을 사용자 지정 합니다.|[File Storage 및 XML Serialization 사용자 지정을](../modeling/customizing-file-storage-and-xml-serialization.md) 참조 하세요.|
|데이터베이스 또는 다른 미디어에 모델을 저장 합니다.|*언어* docdata 재정의<br /><br /> [File Storage 및 XML Serialization 사용자 지정을](../modeling/customizing-file-storage-and-xml-serialization.md) 참조 하세요.|
|여러 Dsl을 통합 하 여 하나의 응용 프로그램의 일부로 작동 하도록 합니다.|[Visual Studio를 사용 하 여 모델 통합 Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)을 참조 하세요.|
|타사에서 DSL을 확장할 수 있도록 허용 하 고 확장을 제어 합니다.|[MEF를 사용하여 DSL 확장](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL 라이브러리를 사용하여 DSL 간에 클래스 공유](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [잠금 정책을 정의하여 읽기 전용 세그먼트 만들기](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>참조

- [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)
- [Domain-Specific 언어를 사용자 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
