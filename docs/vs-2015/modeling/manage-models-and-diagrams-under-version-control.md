---
title: 버전 제어에서 모델 및 다이어그램 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30b13610cc59b8a0225e52abf47f9a4f2cc97d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657572"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>버전 제어에서 모델 및 다이어그램 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

온-프레미스 Team Foundation Server에서 또는 Visual Studio Team Services를 통해 클라우드에서 [Team Foundation 버전 제어 또는 Git를 사용](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314)하여 코드 맵(.dgml 파일)을 비롯한 모델링 프로젝트 및 다이어그램의 여러 버전을 관리합니다.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

> [!IMPORTANT]
> 같은 모델링 프로젝트에서 여러 사용자가 작업할 경우 주의하세요. [중간 규모 또는 대규모 프로젝트에서 모델을 구성](../modeling/structure-your-modeling-solution.md)하는 방법을 살펴보세요.

## <a name="files-in-a-modeling-project"></a><a name="ModelingProjects"></a> 모델링 프로젝트의 파일
 다른 파일에 대한 작업을 수행하는 둘 이상의 사용자가 동시에 한 모델링 프로젝트에서 작업을 수행할 수 있습니다.

 여러 사용자가 수행한 변경 간에 발생하는 충돌을 방지하거나 해결하려면 모델이 파일에 저장되는 방식을 이해해야 합니다.

- 각 패키지는 **ModelDefinition** 프로젝트 폴더에서 유지되는 개별 **.uml** 파일에 저장됩니다. 모델에는 **.uml** 파일도 있습니다. 이러한 파일 중 하나가 삭제되거나 손상되면 해당 패키지 또는 모델이 손실됩니다.

- 각 다이어그램은 두 파일에 저장됩니다. 예를 들어 클래스 다이어그램에는 다음이 포함됩니다.

  - **DiagramName.classdiagram** - 이 파일이 삭제되거나 손상되면 다이어그램이 손실되지만 파일이 표시한 클래스 및 연결은 계속 모델에 포함되고 UML 모델 탐색기에 표시될 수 있습니다.

  - **DiagramName.classdiagram.layout** - 이 파일이 삭제되면 모양도 다이어그램에 계속 나타나지만 크기 및 위치가 손실됩니다. 각 레이아웃 파일은 다이어그램 파일을 보조합니다. 레이아웃 파일을 확인하려면 솔루션 탐색기에서 다이어그램 파일 옆에 있는 [+]를 클릭합니다.

> [!NOTE]
> 파일 간에 일관성을 유지해야 합니다. 예를 들어 소스 제어를 사용하여 .uml 파일에서 변경 내용을 롤백하면 동시에 .*diagram 및 .layout 파일에서 해당 변경 내용을 롤백해야 합니다. 에 표시 되는 요소입니다. \* uml 파일에 표시 되지 않는 다이어그램 파일은 손실 됩니다.

## <a name="working-on-shared-modeling-projects"></a><a name="Shared"></a> 공유 모델링 프로젝트 작업
 프로젝트의 다른 부분에서 수행되는 동시 작업 간 충돌을 최소화하려면:

- 모델링 프로젝트를 서로 다른 작업 영역을 나타내는 패키지로 나눕니다. 전체 모델을 루트 모델에 유지하는 것이 아니라 패키지로 이동합니다. 자세한 내용은 [패키지 및 네임 스페이스 정의](../modeling/define-packages-and-namespaces.md)를 참조 하세요.

- 여러 사용자가 동시에 같은 패키지 또는 다이어그램에서 작업하면 안 됩니다.

- 프로필을 사용할 경우 모든 사용자가 같은 프로필을 설치했는지 확인해야 합니다. [프로필 및 스테레오 타입을 사용 하 여 모델 사용자 지정](../modeling/customize-your-model-with-profiles-and-stereotypes.md)을 참조 하세요.

- 작업 중인 패키지만 변경할 수 있게 하려면:

  - UML 클래스, 구성 요소 또는 사용 사례 다이어그램의 **LinkedPackage** 속성을 설정합니다.

  - UML 모델 탐색기에서 동작 또는 상호 작용을 만들고 바로 패키지로 끌어옵니다. 이 요소는 동작 또는 시퀀스 다이어그램에서 첫 번째 노드를 만들 때 UML 모델 탐색기에 나타납니다.

- 패키지를 계속 추적할 수 있도록 패키지 파일 이름을 바꿔서 실제 패키지 이름을 반영합니다.

- [!INCLUDE[esprscc](../includes/esprscc-md.md)]에서는 항상 개별 파일이 아니라 전체 모델링 프로젝트에서 **체크 인** 및 **최신 버전 가져오기** 작업을 수행합니다.

- 항상 모델링 프로젝트를 체크 인하기 전에 즉시 **가져오기** 작업을 수행합니다.

- 항상 **가져오기** 작업을 수행하기 전에 모든 다이어그램을 닫습니다.

    > [!NOTE]
    > **가져오기**를 수행할 때 파일이 열려 있고 작업으로 인해 로컬 변경이 발생하면 파일을 다시 로드할지 묻는 메시지가 표시됩니다. 이 경우 **아니요**를 클릭하고 전체 프로젝트를 다시 로드합니다. **솔루션 탐색기**에서 모델링 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 업로드**, **프로젝트 다시 로드**를 차례로 클릭합니다.

### <a name="changes-requiring-exclusive-access-to-the-model"></a><a name="Exclusive"></a> 모델에 대 한 단독 액세스를 필요로 하는 변경 내용
 다음과 같은 변경을 수행하기 전에 전체 프로젝트에 체크 아웃 잠금이 있는지 확인하세요.

- 다른 패키지에서 참조되는 요소 이름 바꾸기 및 삭제.

- 패키지 경계를 교차하는 관계의 속성 변경.

- 체크 아웃 잠금에 대해 알아보려면 [파일 체크 아웃 및 편집](https://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a)을 참조하세요.

##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>프로젝트 폴더에 다이어그램 파일을 넣거나 빼려면

1. **Visual Studio용 개발자 명령 프롬프트**를 시작합니다.

2. **tf rename** 을 사용하여 다이어그램 파일과 해당 **.layout** 파일을 이동합니다.

     `tf rename sourcePath targetPath`

3. 솔루션 탐색기에서 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트에서 제외**를 클릭합니다.

4. 대상 폴더에 파일을 추가합니다.

     솔루션 탐색기에서 대상 폴더 또는 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음 **기존 항목**을 클릭합니다. 대화 상자에서 다이어그램 파일을 선택하고 **추가**를 클릭합니다. 레이아웃 파일이 자동으로 추가됩니다.

    > [!NOTE]
    > 파일을 다른 프로젝트로 이동할 수는 없습니다.

## <a name="merging-changes-in-model-files-and-diagrams"></a><a name="Merging"></a> 모델 파일 및 다이어그램에서 변경 내용 병합
 둘 이상의 사용자가 한 모델에서 동시에 작업하고 나면 [!INCLUDE[esprscc](../includes/esprscc-md.md)] 에서는 모델 파일에서 변경 내용을 병합할지 묻는 메시지를 표시합니다. 이전 섹션에서 설명된 대로 개별 프로젝트에서 작업하면 대부분 병합할 필요가 없습니다. 보통 나머지 충돌은 자동으로 안전하게 병합될 수 있습니다. 다음과 같은 변경 내용은 문제를 일으키지 않습니다.

- 수명선 형식. 기존 형식에서 수명선을 만든 경우가 아니면 수명선을 상호 작용(시퀀스 다이어그램)에 추가할 경우 형식이 루트 모델에 저장됩니다.

- 새 동작 및 상호 작용은 처음에 루트 모델에 저장됩니다.

- 요소 및 관계 추가.

- 패키지 내에서만 참조되는 요소 이름 바꾸기 또는 삭제.

## <a name="see-also"></a>관련 항목
 [아키텍처 분석 및 모델링 아키텍처](../modeling/analyze-and-model-your-architecture.md) [공유 모델 및 내보내기 다이어그램](../modeling/share-models-and-exporting-diagrams.md)
