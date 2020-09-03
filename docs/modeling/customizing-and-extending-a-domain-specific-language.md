---
title: 도메인별 언어 사용자 지정 및 확장
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9040e65d3e9acce101ee6b481c2cd27d24285169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597167"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>도메인별 언어 사용자 지정 및 확장

Visual Studio 모델링 및 시각화 SDK (VMSDK)는 모델링 도구를 정의 하는 데 사용할 수 있는 여러 수준을 제공 합니다.

1. DSL 정의 다이어그램을 사용 하 여 DSL (도메인별 언어)을 정의 합니다. 다이어그램 표기법, 읽을 수 있는 XML 형식 및 코드 및 기타 아티팩트를 생성 하는 데 필요한 기본 도구를 사용 하 여 DSL을 빠르게 만들 수 있습니다. 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요.

2. DSL 정의의 고급 기능을 사용 하 여 DSL을 미세 조정 합니다. 예를 들어 사용자가 요소를 만들 때 추가 링크를 표시할 수 있습니다. 이러한 기술은 대부분 DSL 정의에서 수행 되며 일부 프로그램 코드 줄이 필요 합니다.

3. 프로그램 코드를 사용 하 여 모델링 도구를 확장 합니다. VMSDK는 DSL 정의에서 생성된 코드를 사용하여 확장을 쉽게 통합할 수 있도록 설계되었습니다. 자세한 내용은 [도메인별 언어를 사용자 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)을 참조 하세요.

> [!NOTE]
> DSL 정의 파일을 업데이트 한 경우 솔루션을 다시 빌드하기 전에 **솔루션 탐색기** 도구 모음에서 **모든 템플릿 변환** 을 클릭 해야 합니다.

## <a name="article-reference"></a>문서 참조

|이 효과를 얻으려면|이 항목을 참조 하세요.|
|-|-|
|사용자가 모양의 색 및 스타일 속성을 설정할 수 있습니다.|셰이프 또는 연결선 클래스를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가**를 가리킨 다음 항목을 클릭 합니다.|
|모델 요소의 다른 클래스는 다이어그램에서 초기 높이 및 너비, 색, 도구 설명 등의 속성을 공유 하는 것과 비슷합니다.|도형 또는 연결선 클래스 간에 상속을 사용 합니다. 파생 셰이프와 파생 된 도메인 클래스 간의 매핑은 부모의 매핑 정보를 상속 합니다.<br /><br /> 또는 서로 다른 도메인 클래스를 동일한 shape 클래스에 매핑합니다.|
|모델 요소의 클래스는 여러 셰이프 컨텍스트에 의해 표시 됩니다.|둘 이상의 shape 클래스를 동일한 도메인 클래스에 매핑합니다. 솔루션을 빌드할 때 오류 보고서를 따르고 사용할 셰이프를 결정 하는 데 필요한 코드를 제공 합니다.|
|모양 색 또는 글꼴과 같은 기타 기능은 현재 상태를 표시 합니다.|[모델을 반영 하도록 모양 및 연결선 업데이트를](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)참조 하세요.<br /><br /> 노출 된 속성을 업데이트 하는 규칙을 만듭니다. [규칙은 모델 내에서 변경 내용 전파](../modeling/rules-propagate-changes-within-the-model.md)를 참조 하세요.<br /><br /> 또는 OnAssociatedPropertyChanged ()를 사용 하 여 링크 화살표나 글꼴과 같은 노출 되지 않는 기능을 업데이트 합니다.|
|상태를 나타내는 셰이프 변경에 대 한 아이콘입니다.|DSL 세부 정보 창에서 데코레이터 매핑의 표시 여부를 설정 합니다. 동일한 위치에서 여러 이미지 데코레이터를 찾습니다. [모델을 반영 하도록 모양 및 연결선 업데이트를](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)참조 하세요.<br /><br /> 또는를 재정의 `ImageField.GetDisplayImage()` 합니다. 의 예제를 참조 하세요 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|모든 셰이프에 배경 이미지 설정|InitializeInstanceResources ()를 재정의 하 여 고정 된 ImageField을 추가 합니다.|
|모든 깊이에 도형 중첩|재귀 포함 트리를 설정 합니다. 셰이프를 포함 하는 Boundsrules로를 정의 합니다.|
|요소 경계의 고정 지점에서 커넥터를 연결 합니다.|다이어그램에서 작은 포트로 표시 되는 포함 된 터미널 요소를 정의 합니다. Boundsrules로를 사용 하 여 현재 위치의 포트를 수정 합니다. [시각화 및 모델링 SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)에서 회로 다이어그램 샘플을 참조 하세요.|
|텍스트 필드 다른 값에서 파생 된 값을 표시 합니다.|텍스트 데코레이터를 계산 된 저장소 도메인 속성 또는 사용자 지정 저장소 도메인 속성에 매핑합니다. 자세한 내용은 [계산 된 저장소 속성 및 사용자 지정 저장소 속성](../modeling/calculated-and-custom-storage-properties.md)을 참조 하세요.|
|모델 요소 간 또는 모양 사이에 변경 내용 전파|[도메인 특정 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)를 참조 하세요.|
|저장소 외부의 다른 Visual Studio 확장과 같은 리소스에 변경 내용을 전파 합니다.|[이벤트 처리기가 모델 외부에서 변경 내용을 전파 하는](../modeling/event-handlers-propagate-changes-outside-the-model.md)방법을 참조 하세요.|
|속성 창 관련 요소의 속성을 표시 합니다.|속성 전달을 설정 합니다. [속성 창 사용자 지정을](../modeling/customizing-the-properties-window.md)참조 하세요.|
|속성 범주|속성 창은 범주 라는 섹션으로 나뉩니다. 도메인 속성의 **범주** 를 설정 합니다. 동일한 범주 이름을 가진 속성은 같은 섹션에 나타납니다. 관계 역할의 **범주** 를 설정할 수도 있습니다.|
|도메인 속성에 대 한 사용자 액세스 제어|Set **은** 검색 가능 false로 설정 하 여 런타임 시 도메인 속성이 속성 창에 나타나지 않도록 합니다. 텍스트 데코레이터에도 매핑할 수 있습니다.<br /><br /> **UI 읽기 전용은** 사용자가 도메인 속성을 변경할 수 없도록 합니다.<br /><br /> 도메인 속성에 대 한 프로그램 액세스는 영향을 받지 않습니다.|
|DSL의 모델 탐색기에서 노드의 이름, 아이콘 및 표시 여부를 변경 합니다.|[모델 탐색기 사용자 지정을](../modeling/customizing-the-model-explorer.md)참조 하세요.|
|복사, 잘라내기 및 붙여넣기 사용|DSL 탐색기에서 **편집기** 노드의 **복사 붙여넣기 사용** 속성을 설정 합니다.|
|요소가 복사 될 때마다 참조 링크와 해당 대상을 복사 합니다. 예를 들어 항목에 첨부 된 주석을 복사 합니다.|원본 역할의 **전파 복사** 속성을 설정 합니다 (DSL 정의 다이어그램에서 도메인 관계의 한 쪽에 있는 줄로 표시 됨).<br /><br /> 더 복잡 한 효과를 얻기 위해 ProcessOnCopy를 재정의 하는 코드를 작성 합니다.<br /><br /> [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)을 참조 하세요.|
|요소가 삭제 될 때 관련 된 요소를 삭제, 다시 부모 또는 다시 링크 합니다.|관계 역할의 **전파 삭제** 값을 설정 합니다. 더 복잡 한 효과를 위해 `ShouldVisitRelationship` `ShouldVisitRolePlayer` `MyDslDeleteClosure` **DomainModel.cs**에 정의 된 클래스의 및 메서드를 재정의 합니다.|
|복사 및 끌어서 놓기를 통해 셰이프 레이아웃 및 모양을 유지 합니다.|셰이프 및 연결선을 복사 된에 추가 합니다 `ElementGroupPrototype` . 재정의할 가장 편리한 메서드는 `ElementOperations.CreateElementGroupPrototype()`<br /><br /> [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)을 참조 하세요.|
|선택한 위치(예: 현재 커서 위치)에 모양을 붙여넣습니다.|`ClipboardCommandSet.ProcessOnCopy()`위치 별 버전을 사용 하도록 재정의 `ElementOperations.Merge().` 합니다. [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)을 참조 하세요.|
|붙여넣을 때 추가 링크 만들기|Override ClipboardCommandSet. ProcessOnPasteCommand ()|
|이 다이어그램, 다른 Dsl 및 Windows 요소에서 끌어서 놓기 사용|[방법: 끌어서 놓기 처리기 추가를](../modeling/how-to-add-a-drag-and-drop-handler.md) 참조 하세요.|
|셰이프 또는 도구를 부모 페이지로 끌어온 것 처럼 자식 도형으로 끌어 올 수 있습니다.|대상 개체 클래스의 요소 병합 지시문을 정의 하 여 끌어 놓은 개체를 부모로 전달 합니다. [요소 만들기 및 이동 사용자 지정을](../modeling/customizing-element-creation-and-movement.md)참조 하세요.|
|셰이프 또는 도구를 도형으로 끌어 오거나 추가 링크나 개체를 만들 수 있습니다. 예를 들어 주석을 연결할 항목에 주석을 놓을 수 있습니다.|대상 도메인 클래스에 요소 병합 지시문을 정의 하 고 생성할 링크를 정의 합니다. 복잡 한 경우에는 사용자 지정 코드를 추가할 수 있습니다. [요소 만들기 및 이동 사용자 지정을](../modeling/customizing-element-creation-and-movement.md)참조 하세요.|
|도구 하나를 사용 하 여 요소 그룹을 만듭니다. 예를 들어 고정 된 포트 집합을 사용 하는 구성 요소입니다.|ToolboxHelper.cs에서 도구 상자 초기화 메서드를 재정의 합니다. 요소와 해당 관계 링크를 포함 하는 요소 그룹 프로토타입 (요소 그룹 프로토타입)을 만듭니다. [도구 및 도구 상자 사용자 지정을](../modeling/customizing-tools-and-the-toolbox.md)참조 하세요.<br /><br /> 가 중에 주 및 포트 셰이프를 포함 하거나, Boundsrules로를 정의 하 여가 중 p가 인스턴스화될 때 포트 셰이프를 배치 합니다.|
|하나의 연결 도구를 사용 하 여 여러 유형의 관계를 인스턴스화합니다.|도구에서 호출 하는 연결 작성기에 LCD (링크 연결 지시문)를 추가 합니다. Lcd는 두 요소의 형식에서 관계의 형식을 결정 합니다. 요소의 상태에 따라 달라 지도록 사용자 지정 코드를 추가할 수 있습니다. [도구 및 도구 상자 사용자 지정을](../modeling/customizing-tools-and-the-toolbox.md)참조 하세요.|
|스티커 도구-사용자는 도구를 두 번 클릭 하 여 여러 셰이프 또는 연결선을 연속 해 서 만들 수 있습니다.|DSL 탐색기에서 노드를 선택 `Editor` 합니다. 속성 창에서는 **고정 도구 상자 항목을 사용**합니다.|
|메뉴 명령 정의|[방법: 표준 메뉴 명령 수정을](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md) 참조 하세요.|
|유효성 검사 규칙을 사용 하 여 모델 제약|[도메인 특정 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md) 를 참조 하세요.|
|DSL에서 코드, 구성 파일 또는 문서를 생성 합니다.|[도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)|
|모델을 파일에 저장 하는 방법을 사용자 지정 합니다.|[File Storage 및 XML Serialization 사용자 지정을](../modeling/customizing-file-storage-and-xml-serialization.md) 참조 하세요.|
|데이터베이스 또는 다른 미디어에 모델을 저장 합니다.|*언어*docdata 재정의<br /><br /> [File Storage 및 XML Serialization 사용자 지정을](../modeling/customizing-file-storage-and-xml-serialization.md) 참조 하세요.|
|여러 Dsl을 통합 하 여 하나의 응용 프로그램의 일부로 작동 하도록 합니다.|[Visual Studio를 사용 하 여 모델 통합 Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)을 참조 하세요.|
|타사에서 DSL을 확장할 수 있도록 허용 하 고 확장을 제어 합니다.|[MEF를 사용하여 DSL 확장](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL 라이브러리를 사용하여 DSL 간에 클래스 공유](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [잠금 정책을 정의하여 읽기 전용 세그먼트 만들기](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>추가 정보

- [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)
- [도메인 특정 언어를 사용자 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
