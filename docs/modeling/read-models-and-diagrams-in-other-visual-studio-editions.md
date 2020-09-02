---
title: 다른 Visual Studio 버전에서 모델 및 다이어그램 읽기
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebe4cdcefb7b823090cca8976055de5a3ebb9b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595412"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>다른 Visual Studio 버전에서 모델 및 다이어그램 읽기

모델 생성을 지원하지 않는 Visual Studio 버전에서 모델을 열면 읽기 전용 모드로 모델이 열립니다. 이 모드에서는 다이어그램의 레이아웃을 변경할 수 있지만 모델을 변경할 수는 없습니다.

모델 생성을 지 원하는 Visual Studio 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조 하세요.

## <a name="obtaining-access-to-a-model-and-diagrams"></a>모델 및 다이어그램에 대한 액세스 권한 얻기

종속성 다이어그램을 읽으려면 먼저 Visual Studio를 사용 하 여 모델링 프로젝트를 연 다음 그 안에 있는 다이어그램을 열어야 합니다.

이러한 이유로 종속성 다이어그램을 읽으려면 해당 다이어그램을 만든 모델링 프로젝트에도 액세스할 수 있어야 합니다. 원본 제어에서 프로젝트에 액세스 하거나 프로젝트 파일의 복사본을 가져와이 작업을 수행할 수 있습니다.

> [!NOTE]
> 코드 맵 및 코드에서 생성된 .NET 클래스 다이어그램에는 적용되지 않습니다. 이러한 다이어그램은 모델링 프로젝트와 독립적으로 볼 수 있습니다.

종속성 다이어그램을 읽으려면 필요한 최소 파일 집합은 다음과 같습니다.

- 읽을 다이어그램에 대 한 두 개의 다이어그램 파일입니다 (예: **Mydiagram 다이어그램 및 MyDiagram**). 레이아웃.

    > [!NOTE]
    > 종속성 다이어그램의 경우 이름이 _mydiagram_**.layerdiagram.suppressions**인 파일도 있어야 합니다.

- 모델링 프로젝트 파일 (**mymodel**)

- 루트 모델 파일 (**ModelDefinition\MyModel.uml**)

- 다이어그램에서 참조 되는 패키지에 대 한 패키지 파일 (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>읽기 전용 모드에서 수행할 수 있는 변경 내용

모델 생성을 지원하지 않는 Visual Studio 버전에서 모델 및 다이어그램을 열면 모델을 변경할 수 없습니다. 즉, 다이어그램이나 모델 탐색기에 표시되는 요소 및 관계를 변경할 수 없습니다. 그러나 다음과 같이 다이어그램의 레이아웃을 일부 변경할 수 있습니다.

- 다이어그램에서 모양 및 연결선을 다시 정렬합니다.

- 모양을 확장 및 축소합니다.

이러한 변경 내용을 저장할 수 있습니다. 다른 사용자에 게 변경 내용을 표시 하려면 적어도 업데이트 된 **. 레이아웃** 파일을 보내야 합니다.

## <a name="see-also"></a>추가 정보

- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [앱용 모델 만들기](../modeling/create-models-for-your-app.md)
