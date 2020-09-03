---
title: 다른 Visual Studio 버전에서 모델 및 다이어그램 읽기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6a7c944eb3d5378ad0fc1542b90ad182f7eb976
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671283"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>다른 Visual Studio 버전에서 모델 및 다이어그램 읽기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모델 생성을 지원하지 않는 Visual Studio 버전에서 모델을 열면 읽기 전용 모드로 모델이 열립니다. 이 모드에서는 다이어그램의 레이아웃을 변경할 수 있지만 모델을 변경할 수는 없습니다.

 모델 생성을 지 원하는 Visual Studio 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조 하세요.

## <a name="obtaining-access-to-a-model-and-diagrams"></a>모델 및 다이어그램에 대한 액세스 권한 얻기
 UML 다이어그램 또는 레이어 다이어그램을 읽으려면 먼저 Visual Studio를 사용하여 모델링 프로젝트를 연 다음 프로젝트 안에서 다이어그램을 열어야 합니다.

 이런 이유로 UML 다이어그램 또는 레이어 다이어그램을 읽으려면 다이어그램이 생성된 모델링 프로젝트에 대한 액세스 권한도 있어야 합니다. 이 작업을 수행하려면 [!INCLUDE[esprscc](../includes/esprscc-md.md)]에서 프로젝트에서 액세스하거나 프로젝트 파일의 복사본을 가져옵니다.

> [!NOTE]
> 코드 맵 및 코드에서 생성된 .NET 클래스 다이어그램에는 적용되지 않습니다. 이러한 다이어그램은 모델링 프로젝트와 독립적으로 볼 수 있습니다.

 UML 다이어그램 또는 레이어 다이어그램을 읽는 데 필요한 최소 파일 집합은 다음과 같습니다.

- 읽을 다이어그램에 대 한 두 개의 다이어그램 파일입니다 (예: **Mydiagram 다이어그램 및 MyDiagram**). 레이아웃.

    > [!NOTE]
    > 레이어 다이어그램의 경우 이름이 _mydiagram_**.layerdiagram.suppressions**인 파일도 있어야 합니다.

- 모델링 프로젝트 파일 (**mymodel**)

- 루트 모델 파일 (**ModelDefinition\MyModel.uml**)

- 다이어그램에서 참조 되는 패키지에 대 한 패키지 파일 (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>읽기 전용 모드에서 수행할 수 있는 변경 내용
 모델 생성을 지원하지 않는 Visual Studio 버전에서 모델 및 다이어그램을 열면 모델을 변경할 수 없습니다. 즉, 다이어그램이나 모델 탐색기에 표시되는 요소 및 관계를 변경할 수 없습니다. 그러나 다음과 같이 다이어그램의 레이아웃을 일부 변경할 수 있습니다.

- 다이어그램에서 모양 및 연결선을 다시 정렬합니다.

- 모양을 확장 및 축소합니다.

  이러한 변경 내용을 저장할 수 있습니다. 다른 사용자에 게 변경 내용을 표시 하려면 적어도 업데이트 된 **. 레이아웃** 파일을 보내야 합니다.

## <a name="related-topics"></a><a name="RelatedTopics"></a> 관련 항목

|제목|설명|
|-----------|-----------------|
|[레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)|레이어 다이어그램에는 기존 아키텍처 또는 제안된 아키텍처의 구조가 표시됩니다. 코드가 작성되면 레이어 다이어그램에 대해 자동으로 유효성을 검사할 수 있습니다.|
|[UML 동작 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)|동작 다이어그램에는 비즈니스 프로세스 또는 소프트웨어의 작업 흐름이 표시됩니다.|
|[UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)|클래스 다이어그램에는 코드, 데이터베이스 스키마, 통신 프로토콜 또는 비즈니스 도메인 설명에 사용되는 용어집과 같은 여러 컨텍스트에서 사용되는 형식 및 관계가 표시됩니다.|
|[UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)|구성 요소 다이어그램에는 소프트웨어 디자인의 분리 가능 파트 및 해당 인터페이스가 표시됩니다.|
|[UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)|시퀀스 다이어그램에는 소프트웨어 디자인의 요소 간 상호 작용이 표시됩니다.|
|[UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)|사용 사례 다이어그램에는 시스템 사용자 및 특정 목표를 달성하기 위해 수행할 수 있는 동작이 표시됩니다.|

## <a name="see-also"></a>관련 항목
 [앱용 모델 만들기](../modeling/create-models-for-your-app.md)
