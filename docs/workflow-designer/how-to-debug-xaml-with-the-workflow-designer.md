---
title: '워크플로 디자이너: 디버그 XAML'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9be7c8da251a9698e0fceba64e3941ba8fbdf803
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817517"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>방법: Workflow Designer로 XAML 디버그

워크플로는 XAML로 정의됩니다. 워크플로의 UI 표현은 해당 워크플로를 정의하는 XAML 트리의 맨 위에 빌드됩니다. 디버깅 환경은 워크플로 디자이너에서 워크플로를 디버깅 하는 것과 비슷합니다. 예를 들어 XAML을 디버그 하는 동안 지역, 조사식 및 스레드 창은 디버깅 워크플로 디자이너와 동일한 방식으로 작동 합니다. 또한 XAML 디버깅 중의 호출 스택 보기는 워크플로에 대한 실행 흐름의 줄 기반 계층 보기입니다.

> [!NOTE]
> 워크플로의 XAML이 활동과 동일한 어셈블리에 있는 경우 클래스 이름의 어셈블리 부분이 포함되지 않습니다. 클래스 (활동) 이름 중이 부분이 없으면 런타임에 XAML을 로드할 수 없습니다. 기본 프로젝트와 같은 네임스페이스에 활동을 정의하지 않는 것이 좋습니다. 그렇지 않으면 XAML을 디자이너에서 편집한 후에 수작업으로 편집해야 합니다.

## <a name="to-debug-workflow-xaml"></a>워크플로 XAML을 디버깅하려면

1. Visual Studio에서 워크플로 또는 활동 프로젝트를 엽니다.

2. [방법: 워크플로에 중단점 설정](../workflow-designer/how-to-set-breakpoints-in-workflows.md)에 설명 된 대로 디버깅 하려는 작업에 중단점을 설정 합니다.

3. 워크플로 정의가 포함 된 .xaml 파일을 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 선택 합니다. 디자인 뷰에서 중단점을 설정한 활동의 XAML 요소 선언과 같은 줄에 중단점이 표시됩니다.

4. [디버그 워크플로](debugging-workflows-with-the-workflow-designer.md)에 설명 된 대로 디버거를 호출 합니다.

5. 코드 실행이 중단점 중 하나에 도달하면 해당 중단점과 연결된 XAML 요소가 강조 표시됩니다. 다음 중단점으로 이동 하려면 **F10** 또는 **F11** 키를 사용 합니다.

## <a name="see-also"></a>추가 정보

- [방법: 워크플로에 중단점 설정](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [워크플로 디버깅](debugging-workflows-with-the-workflow-designer.md)
