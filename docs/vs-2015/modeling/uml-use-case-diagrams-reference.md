---
title: 'UML 사용 사례 다이어그램: 참조 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbea61c2a26b1dc81487365ef8fc3f320ac95943
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657299"
---
# <a name="uml-use-case-diagrams-reference"></a>UML 사용 사례 다이어그램: 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 *사용 사례 다이어그램* 은 응용 프로그램 또는 시스템을 사용 하는 사용자와이를 사용 하 여 수행할 수 있는 작업을 요약 합니다. UML 사용 사례 다이어그램을 만들려면 **아키텍처** 메뉴에서 **새 UML 또는 레이어 다이어그램**을 클릭 합니다.

 사용 사례 다이어그램은 사용자 요구 사항 설명에 대한 포커스 역할을 합니다. 요구 사항, 사용자 및 주요 구성 요소 간의 관계를 설명합니다. 요구 사항을 자세히 설명하지는 않습니다. 이는 각 사용 사례에 연결될 수 있는 문서 또는 별도 다이어그램에서 설명할 수 있습니다. 사용 사례 다이어그램이 사용자 요구를 이해 하 고 논의 하 고 전달 하는 데 도움이 되는 방법에 대 한 자세한 내용은 [사용자 요구 사항 모델링](../modeling/model-user-requirements.md)을 참조 하세요.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

> [!NOTE]
> 이 항목에서는 사용 사례 다이어그램에서 사용할 수 있는 요소에 대해 설명합니다. 사용 사례 다이어그램을 그리는 방법에 대 한 자세한 내용은 [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)을 참조 하세요. 모델링 다이어그램을 만들고 그리는 방법에 대 한 자세한 내용은 [UML 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md)을 참조 하세요.

## <a name="reading-use-case-diagrams"></a>사용 사례 다이어그램 읽기
 다음 섹션의 표에서는 사용 사례 다이어그램에 사용할 수 있는 요소 및 주요 속성에 대해 설명합니다. 속성의 전체 목록은 [UML 사용 사례 다이어그램 요소의 속성](../modeling/properties-of-elements-on-uml-use-case-diagrams.md)을 참조 하세요.

### <a name="actors-use-cases-and-subsystems"></a>행위자, 사용 사례 및 하위 시스템
 ![사용 사례 다이어그램의 요소](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

|**도형**|**Element**|**설명 및 주요 속성**|
|---------------|-----------------|-----------------------------------------|
|1|**배우**|애플리케이션 또는 시스템을 조작하는 사용자, 조직 또는 외부 시스템을 나타냅니다. 행위자는 형식의 한 종류입니다.<br /><br /> -   **이미지 경로** -기본 행위자 아이콘 대신 사용 해야 하는 이미지의 파일 경로입니다. 아이콘은 Visual Studio 프로젝트 내의 리소스 파일이어야 합니다.|
|2|**사용 사례**|특정 목표를 위해 하나 이상의 행위자가 수행하는 작업을 나타냅니다. 사용 사례는 형식의 한 종류입니다.<br /><br /> -   **주제** -사용 사례가 표시 되는 하위 시스템입니다.|
|3|**연결**|행위자가 사용 사례에 참여함을 나타냅니다.|
|4|**하위 시스템 또는 구성 요소**|작업 중인 시스템 또는 애플리케이션이나 그 일부입니다. 대규모 네트워크에서 애플리케이션의 단일 클래스까지 모든 항목일 수 있습니다.<br /><br /> 시스템 또는 구성 요소가 지원하는 사용 사례는 사각형 안에 표시됩니다. 시스템의 범위를 명확하게 설명하기 위해 일부 사용 사례를 사각형 밖에 표시하는 것이 유용할 수 있습니다.<br /><br /> 사용 사례 다이어그램의 하위 시스템은 기본적으로 구성 요소 다이어그램의 구성 요소와 동일한 형식입니다.<br /><br /> -   **간접적으로 인스턴스화 됨** -false 인 경우 실행 중인 시스템에이 하위 시스템에 직접 해당 하는 개체가 하나 이상 있습니다. true이면 하위 시스템이 해당 구성 파트의 인스턴스화를 통해서만 실행 중인 시스템에 나타나는 디자인 구문입니다.|

### <a name="structuring-use-cases"></a>사용 사례 구성
 ![포함, 확장 및 일반화가 포함된 사용 사례](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")

|도형|**Element**|설명|
|-----------|-----------------|-----------------|
|5|**되어야**|포함하는 사용 사례는 포함된 사용 사례를 호출합니다. 포함은 사용 사례가 더 작은 단계로 구분되는 방식을 표시하는 데 사용됩니다. 포함된 사용 사례가 화살촉 끝에 있습니다.<br /><br /> 단계 순서는 다이어그램에 표시되지 않습니다. 동작 다이어그램, 시퀀스 다이어그램 또는 다른 문서를 사용하여 이러한 세부 정보를 설명할 수 있습니다.|
|6|**연장**|확장 사용 사례는 확장된 사용 사례에 목표 및 단계를 추가합니다. 확장은 특정 조건에서만 작동합니다. 확장된 사용 사례가 화살촉 끝에 있습니다.<br /><br /> 확장이 적용되는 정확한 상황은 다이어그램에 표시되지 않습니다. 주석 또는 다른 문서에 기록할 수 있습니다.|
|7|**상속**|특수화된 요소 및 일반화된 요소와 관련이 있습니다. 일반화된 요소가 화살촉 끝에 있습니다.<br /><br /> 특수화된 사용 사례는 일반화의 목표와 행위자를 상속하며, 보다 구체적인 목표와 이러한 목표를 달성하기 위한 단계를 추가할 수 있습니다.<br /><br /> 특수화된 행위자는 해당 일반화의 사용 사례, 특성 및 연결을 상속하며 더 추가할 수 있습니다.|
|8|**종속성**|소스 디자인이 대상 디자인에 따라 달라짐을 나타냅니다.|
|9|**설명**|다이어그램에 일반 메모를 추가하는 데 사용됩니다.|
|10|**아티팩트**|아티팩트는 다른 다이어그램 또는 문서에 대한 링크를 제공합니다. 솔루션 탐색기에서 파일을 끌어 만들 수 있습니다. 다이어그램의 다른 요소에 종속성으로 연결될 수 있습니다. 아티팩트는 일반적으로 자세히 설명하는 시퀀스 다이어그램, OneNote 페이지, Word 문서 또는 PowerPoint 프레젠테이션에 사용 사례를 연결하는 데 사용됩니다. 문서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션의 항목 또는 SharePoint 사이트와 같은 공유 위치의 문서일 수 있습니다.<br /><br /> -   **하이퍼링크**. 다이어그램 또는 문서의 URL 또는 파일 경로입니다.<br /><br /> 아티팩트를 두 번 클릭하여 연결하는 파일 또는 웹 페이지를 엽니다.|
|11(표시되지 않음)|**패키지**|패키지 내에 사용 사례, 행위자 및 하위 시스템을 함께 포함할 수 있습니다. 패키지 셰이프는 다이어그램에 표시 되지 않지만 다이어그램의 **LinkedPackage** 속성을 설정할 수 있습니다. 다이어그램에서 이후에 만드는 요소는 패키지 내에 배치됩니다. 자세한 내용은 [패키지 및 네임 스페이스 정의](../modeling/define-packages-and-namespaces.md)를 참조 하세요.|

## <a name="see-also"></a>관련 항목
 [Uml 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md) [uml 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md) [Uml 시퀀스 다이어그램](../modeling/uml-sequence-diagrams-reference.md) : Uml [클래스 다이어그램](../modeling/uml-class-diagrams-reference.md) 참조: Uml [구성](../modeling/uml-component-diagrams-reference.md) 요소 다이어그램 참조: uml [구성 요소 다이어그램](../modeling/uml-component-diagrams-reference.md) 참조: 참조
