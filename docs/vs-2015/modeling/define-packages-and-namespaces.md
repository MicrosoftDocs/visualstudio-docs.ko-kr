---
title: 패키지 및 네임 스페이스 정의 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 657bb91295134352fb00649ad06f59e34593c578
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669909"
---
# <a name="define-packages-and-namespaces"></a>패키지 및 네임스페이스 정의
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 *패키지* 는 클래스, 사용 사례 및 구성 요소와 같은 UML 요소 정의에 대 한 컨테이너입니다. 패키지가 다른 패키지를 포함할 수도 있습니다.

 UML 모델 탐색기에서 패키지 내의 모든 정의는 패키지 아래에 중첩됩니다. UML 모델은 패키지의 한 종류이며 트리의 루트를 구성합니다.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="in-this-topic"></a>항목 내용
 [네임스페이스](#Namespaces)

 [패키지 만들기 및 보기](#Packages)

 [패키지 내에 모델 요소 만들기](#Elements)

 [패키지 안이나 밖으로 요소 이동](#Moving)

 [패키지에 요소 붙여넣기](#Pasting)

 [패키지 간의 관계 가져오기](#Import)

 [네임스페이스 간 참조](#References)

 [패키지 속성](#Properties)

## <a name="namespaces"></a><a name="Namespaces"></a> 네임 스페이스
 패키지는 작업을 여러 영역으로 분리하는 데 유용합니다. 각 패키지는 서로 다른 패키지에 정의된 이름이 서로 충돌하지 않도록 네임스페이스를 정의합니다.

 각 요소의 정규화된 이름 속성은 요소가 속한 패키지의 정규화된 이름 및 요소 자체의 이름입니다. 예를 들어 패키지가 `MyPackage`이면 패키지 내의 클래스는 `MyPackage::MyClass`와 같은 정규화된 이름을 갖습니다. 모든 요소가 모델 내에 포함되기 때문에 모든 정규화된 이름은 모델 이름으로 시작합니다.

 또한 모델은 모델에 있는 모든 요소의 정규화된 이름이 모델 이름으로 시작하도록 네임스페이스를 정의합니다.

 다른 모델 요소도 네임스페이스를 정의합니다. 예를 들어 작업은 정규화된 이름이 `MyModel ::MyPackage ::MyClass ::MyOperation`과 같도록 부모 클래스에서 정의된 네임스페이스에 속합니다. 동일한 방식으로 동작은 부모 동작에서 정의된 네임스페이스에 속합니다.

 패키지는 컨테이너입니다. 패키지를 이동하거나 삭제하는 경우 패키지 내에 정의된 클래스, 패키지 및 기타 항목도 이동 또는 삭제됩니다. 네임스페이스를 정의하는 다른 요소의 경우도 마찬가지입니다.

## <a name="creating-and-viewing-packages"></a><a name="Packages"></a> 패키지 만들기 및 보기
 UML 클래스 다이어그램 또는 UML 모델 탐색기에서 패키지를 만들 수 있습니다.

#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>UML 클래스 다이어그램에서 패키지를 만들려면

1. UML 클래스 다이어그램을 열거나 새로 만듭니다.

2. **패키지** 도구를 클릭 합니다.

3. 다이어그램에서 아무 곳이나 클릭합니다. 새 패키지 모양이 나타납니다.

     기존 패키지 내부를 클릭하여 한 패키지를 다른 패키지 안에 중첩할 수 있습니다.

4. 패키지의 새 이름을 입력합니다.

#### <a name="to-create-a-package-in-uml-model-explorer"></a>UML 모델 탐색기에서 패키지를 만들려면

1. **UML 모델 탐색기**를 엽니다. **아키텍처** 메뉴에서 **창**을 가리킨 다음 **UML 모델 탐색기**를 클릭 합니다.

2. 새 패키지를 추가할 패키지 또는 모델을 마우스 오른쪽 단추로 클릭합니다.

   > [!NOTE]
   > 다른 패키지 안에 패키지를 중첩할 수 있습니다.

3. **추가** 를 가리킨 다음 **패키지**를 클릭 합니다.

    새 패키지가 모델에 나타납니다.

4. 패키지의 새 이름을 입력합니다.

   UML 모델 탐색기에서 패키지를 만든 경우 UML 클래스 다이어그램에 표시할 수 있습니다. 두 개 이상의 UML 클래스 다이어그램에 패키지를 표시할 수도 있습니다.

#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>UML 클래스 다이어그램에 기존 패키지를 표시하려면

- UML 모델 탐색기에서 클래스 다이어그램으로 패키지를 끌어옵니다.

    > [!NOTE]
    > 이 다이어그램에서 패키지 뷰가 생성됩니다. 패키지에 포함된 모든 요소가 반드시 표시되는 것은 아닙니다. 모든 패키지의 내용을 보려면 UML 모델 탐색기에서 표시합니다.

## <a name="creating-model-elements-inside-packages"></a><a name="Elements"></a> 패키지 내에 모델 요소 만들기
 패키지 내에 모델 요소를 배치할 수 방법에는 4가지가 있습니다.

- UML 모델 탐색기에서 패키지에 새 요소를 추가합니다.

- UML 클래스 다이어그램에서 패키지에 클래스와 기타 형식을 추가합니다.

- 다이어그램에서 만든 새 요소가 지정 하는 패키지 내에 배치 되도록 다이어그램의 **LinkedPackage** 속성을 설정 합니다. 클래스 다이어그램, 구성 요소 다이어그램 및 사용 사례 다이어그램을 이런 방식으로 패키지에 연결할 수 있습니다.

- UML 모델 탐색기에서 패키지 안이나 밖으로 요소를 이동합니다.

  패키지의 요소는 UML 모델 탐색기에서 패키지 아래에 표시되고, 정규화된 이름이 패키지의 정규화된 이름으로 시작합니다. 요소의 정규화 된 이름을 보려면 요소를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. **정규화 된 이름** 속성이 **속성** 창에 나타납니다.

#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>UML 모델 탐색기에서 패키지의 요소를 만들려면

1. **UML 모델 탐색기**를 엽니다. **보기** 메뉴에서 **다른 창**을 가리킨 다음 **UML 모델 탐색기**를 클릭 합니다.

2. 새 요소를 추가할 패키지 또는 모델을 마우스 오른쪽 단추로 클릭합니다.

3. **추가**를 가리킨 다음 추가할 요소의 종류를 클릭 합니다.

     새 요소가 패키지 아래에 나타납니다.

4. 새 요소의 이름을 입력합니다.

    > [!NOTE]
    > 새 요소는 다이어그램에 나타나지 않습니다. 새 요소의 뷰를 만들기 위해 UML 모델 탐색기에서 다이어그램으로 끌어올 수 있습니다. 다이어그램이 이러한 종류의 요소를 표시하는 형식이어야 합니다.

#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>UML 클래스 다이어그램에서 패키지의 요소를 만들려면

1. 패키지가 표시되는 클래스 다이어그램을 엽니다.

    - 아직 수행하지 않은 경우 새 패키지를 만듭니다.

    - 기존 패키지가 클래스 다이어그램에 표시 되도록 하려면 **UML 모델 탐색기** 에서 클래스 다이어그램으로 패키지를 끌어 옵니다.

2. 클래스, 인터페이스, 열거형 또는 패키지에 대한 도구를 클릭합니다.

3. 새 요소를 배치할 패키지를 클릭합니다.

     새 요소가 패키지 내에 나타납니다.

#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>지정된 패키지에서 다이어그램의 모든 요소를 만들려면

1. 아직 수행하지 않은 경우 패키지를 만듭니다.

2. 구성 요소 다이어그램, 사용 사례 다이어그램 또는 UML 클래스 다이어그램을 엽니다.

3. 다이어그램의 속성을 엽니다. 다이어그램의 빈 부분을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

4. **연결 된 패키지** 속성에서 다이어그램의 콘텐츠를 포함 하려는 패키지를 선택 합니다.

5. 다이어그램에서 새 요소를 만듭니다. 패키지에 배치됩니다.

    - 각 요소의 **정규화 된 이름은** 패키지의 정규화 된 이름으로 시작 됩니다.

    - **UML 모델 탐색기**에서 각 요소는 패키지 아래에 나타납니다.

## <a name="moving-elements-into-and-out-of-packages"></a><a name="Moving"></a> 패키지에서/외부로 요소 이동
 하나 이상의 요소를 패키지 안이나 밖으로 이동할 수 있습니다.

 패키지를 이동하는 경우 안에 있는 모든 항목도 함께 이동됩니다.

#### <a name="to-move-an-element-into-or-out-of-a-package"></a>패키지 안이나 밖으로 요소를 이동하려면

- UML 모델 탐색기에서 루트가 패키지인 트리 안이나 밖으로 요소를 끕니다.

     요소의 정규화된 이름이 새 소유 패키지 또는 모델을 표시하도록 변경됩니다.

     \- 또는 -

- 클래스 다이어그램에서 요소를 패키지 모양으로 끌어옵니다.

     요소의 정규화된 이름이 새 소유 패키지를 표시하도록 변경됩니다.

    > [!NOTE]
    > 패키지에서 다이어그램의 빈 부분으로 요소를 끌어오면 소유 패키지가 변경되지 않습니다. 이렇게 하면 패키지 자체를 표시하지 않고 여러 패키지의 요소를 보여 주는 다이어그램을 만들 수 있습니다.

## <a name="pasting-elements-into-a-package"></a><a name="Pasting"></a> 패키지에 요소 붙여넣기
 패키지에 요소를 붙여넣을 수 있습니다. 관련된 요소 그룹을 패키지에 붙여넣으면 요소 간의 관계도 붙여넣어집니다.

#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>UML 클래스 다이어그램에서 패키지에 요소를 붙여넣으려면

1. UML 클래스 다이어그램에서 복사할 요소를 모두 선택합니다. 그 중 하나를 마우스 오른쪽 단추로 클릭 한 다음 **복사**를 클릭 합니다.

2. 패키지를 마우스 오른쪽 단추로 클릭 한 다음 **붙여넣기**를 클릭 합니다.

    > [!NOTE]
    > 패키지는 다른 다이어그램에 있을 수 있습니다.

## <a name="import-relationships-between-packages"></a><a name="Import"></a> 패키지 간 관계 가져오기
 **가져오기** 도구를 사용 하 여 패키지 간의 가져오기 관계를 정의할 수 있습니다.

 가져오기는 가져온 패키지에서 정의된 요소, 즉 관계의 화살표 끝 요소가 가져오는 패키지에서도 효과적으로 정의됨을 의미합니다. 표시 유형이 **package** 로 정의 되어 있는 모든 요소는 가져오기 패키지에도 표시 됩니다.

 가져오기 관계에 루프를 만들지 마세요.

## <a name="references-from-one-namespace-to-another"></a><a name="References"></a> 한 네임 스페이스에서 다른 네임 스페이스에 대 한 참조
 패키지 간에 요소를 참조하려는 경우 요소의 정규화된 이름을 사용해야 합니다.

 예를 들어 패키지의 `SalesCommon`이 `CustomerAddress` 형식을 정의한다고 가정합니다. 다른 패키지의 `RestaurantSales`에서 고객 주소 형식의 특성을 가진 `MealOrder` 형식을 정의하려고 합니다. 다음 두 가지 옵션을 사용할 수 있습니다.

- 정규화된 이름 `SalesCommon::CustomerAddress`를 사용하여 특성의 형식을 지정합니다. 이 작업은 `CustomerAddress` **표시 유형** 속성이 **Public**으로 설정 된 경우에만 가능 합니다.

- `RestaurantSales` 패키지에서 `SalesCommon` 패키지로 가져오기 관계를 만듭니다. 그런 다음 정규화된 이름을 사용하지 않고 `CustomerAddress`를 사용할 수 있습니다.

## <a name="properties-of-packages"></a><a name="Properties"></a> 패키지 속성
 각 패키지에는 다음과 같은 속성이 있습니다. 속성을 보려면 다이어그램 또는 UML 모델 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

|속성|기본값|설명|
|--------------|-------------------|-----------------|
|**이름**|(새 이름)|패키지 이름. 다이어그램 또는 속성 창에서 변경할 수 있습니다.|
|**정규화된 이름**|*Container* :: *package name*|이 패키지를 포함하는 패키지 또는 모델의 이름이 접두사로 추가된 전체 이름입니다. 자세한 내용은 [네임스페이스](#Namespaces)를 참조하세요.|
|**프로필**|(비어 있음)|이 패키지에 연결된 프로필의 목록입니다. 이러한 프로필은 패키지 내의 요소에 적용할 수 있는 스테레오타입을 제공합니다. 자세한 내용은 [프로필 및 스테레오 타입을 사용 하 여 모델 사용자 지정](../modeling/customize-your-model-with-profiles-and-stereotypes.md)을 참조 하세요.|
|**표시 유형**|**공용**|부모 패키지 외부에서 패키지의 표시 유형입니다.|
|**작업 항목**|(비어 있음)|연결된 작업 항목의 목록입니다. 자세한 내용은 [모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)을 참조 하세요.|
|**정의 위치**|(이름)|패키지의 세부 정보가 저장되는 파일 이름입니다. 파일이 **Modeldefinition** 프로젝트 폴더 내에 있습니다. 이 정보는 소스 제어 용도에 유용할 수 있습니다.|
|**설명**|(비어 있음)|패키지에 대한 설명입니다.|
|**스테레오타입**|(비어 있음)|이 패키지에 적용되는 스테레오타입입니다. 사용 가능한 스테레오타입 목록은 이 패키지와 이 패키지를 포함하는 패키지에 대해 선택한 프로필에 의해 결정됩니다. 자세한 내용은 [프로필 및 스테레오 타입을 사용 하 여 모델 사용자 지정](../modeling/customize-your-model-with-profiles-and-stereotypes.md)을 참조 하세요.|

## <a name="how-packages-are-stored"></a>패키지 저장 방식
 새 패키지를 만들 때 **Modeldefinition** 프로젝트 폴더에 새 **uml** 파일이 만들어집니다. 패키지 이기도 한 루트 모델도 **. uml** 파일에 저장 됩니다.

 또한 각 다이어그램은 다이어그램의 모양을 나타내는 파일 두 개와 셰이프 위치를 기록 하는 **. 레이아웃** 파일에 저장 됩니다.

## <a name="see-also"></a>관련 항목
 Uml [모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md) [uml 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md) [uml 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md) [버전 제어에서 모델 및 다이어그램 관리](../modeling/manage-models-and-diagrams-under-version-control.md)
