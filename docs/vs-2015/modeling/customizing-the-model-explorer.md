---
title: 모델 탐색기 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce96f2a3df901c1fea0aa4caa97d29c07db5e681
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654948"
---
# <a name="customizing-the-model-explorer"></a>모델 탐색기 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음과 같이 도메인별 언어 디자이너에 대 한 탐색기의 모양과 동작을 변경할 수 있습니다.

- 창 제목을 변경 합니다.

- 탭 아이콘을 변경 합니다.

- 노드의 아이콘을 변경 합니다.

- 노드를 숨깁니다.

## <a name="changing-the-window-title"></a>창 제목 변경
 생성 된 탐색기의 창 제목을 변경 하려면 **DSL 탐색기**에서 **탐색기 동작** 을 선택 하 고 **속성** 창에서 **제목** 속성을 원하는 제목으로 설정 합니다.

## <a name="changing-the-tab-icon"></a>탭 아이콘 변경
 탐색기의 탭 아이콘을 변경 하려면 .bmp 파일에서 16x16 픽셀 아이콘을 사용 합니다. \DslPackage\Resources\ 폴더에 아이콘 파일을 입력 한 다음 파일 이름을 **ModelExplorerToolWindowBitmaps.bmp**로 변경 합니다. 예를 들어, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .ico 아이콘 파일을 .bmp 형식으로 변경 하 고 **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**로 이름을 바꿀 수 있습니다. 생성 된 디자이너는 **솔루션 탐색기**와 함께 도킹할 때 탐색기의 탭에이 아이콘을 표시 합니다.

## <a name="setting-custom-icons-on-explorer-nodes"></a>탐색기 노드에 사용자 지정 아이콘 설정
 탐색기 노드 설정을 사용 하 여 탐색기에서 노드를 사용자 지정할 수 있습니다. 다음 절차에서는 노드에 아이콘을 추가 하는 방법을 보여 줍니다.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>탐색기 노드에 아이콘을 추가 하려면

1. [!INCLUDE[dsl](../includes/dsl-md.md)]작업 흐름 솔루션 템플릿을 사용 하 여 솔루션을 만듭니다.

2. 솔루션의 **Dsl\resources** 폴더에 16x16 픽셀 아이콘이 포함 된 .bmp 파일을 배치 합니다.

3. **DSL 탐색기**에서 **탐색기 동작** 을 마우스 오른쪽 단추로 클릭 한 다음 **새 탐색기 노드 설정 추가**를 클릭 합니다.

     **사용자 지정 노드 설정** 노드 아래에 **ExplorerNodeSettings** 노드가 나타납니다.

4. **ExplorerNodeSettings**을 선택 하 고 **속성** 창에서 **클래스** 를 **행위자**로 설정 합니다.

5. 아이콘 파일의 경로에 **표시 되도록 아이콘을** 설정 합니다.

6. 모든 템플릿을 변환한 다음 솔루션을 빌드하고 실행 합니다.

7. 생성 된 디자이너에서 샘플 다이어그램을 엽니다.

     탐색기에는 아이콘을 포함 하는 세 개의 **행위자** 노드가 표시 됩니다.

> [!NOTE]
> 생성 된 탐색기에 표시 되는 요소에 대해 노드 아이콘을 설정 하면 모든 탐색기 노드에 아이콘이 표시 됩니다. 아이콘을 설정 하지 않으면 노드에 기본 아이콘이 표시 됩니다.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>탐색기 노드에 표시 되는 이름 변경
 탐색기에서 모델 요소의 이름이 표시 되는 방식을 변경할 수 있습니다. 다음 절차에서는 주석 노드의 **주석** 에서 참조 하는 **작업** 의 이름을 표시 하는 방법을 보여 줍니다.

#### <a name="to-display-a-property"></a>속성을 표시 하려면

1. 이전 절차에서 만든 솔루션을 엽니다.

2. 속성 이름 **주체가** 0 ..1 인 역할의 복합성을 설정 하 여 **주석이** 단일 도메인 클래스만 참조 하는지 확인 합니다. 속성 이름이 **제목이**되어야 하 고 관계 이름이 **CommentReferencesSubject**됩니다.

3. **DSL 탐색기**에서 **탐색기 동작** 을 마우스 오른쪽 단추로 클릭 한 다음 **새 탐색기 노드 설정 추가**를 클릭 합니다.

     **사용자 지정 노드 설정** 노드 아래에 **ExplorerNodeSettings** 노드가 나타납니다.

4. **ExplorerNodeSettings**을 선택 하 고 **속성** 창에서 **클래스** 를 **주석**으로 설정 합니다.

5. **주석** 노드를 마우스 오른쪽 단추로 클릭 한 다음 **새 속성 경로 추가**를 클릭 합니다.

     라는 명명 된 **속성이 표시**된 새 노드가 표시 됩니다.

6. **표시 되는 속성**을 선택 하 고 **속성 창에서** **속성 경로**의 값 필드를 클릭 합니다. **설명**, **CommentReferencesSubject**, **flowelement**를 차례로 선택 합니다. 결과 경로는 **CommentReferencesSubject/!와 비슷합니다. 제목**.

7. **속성**의 값 필드에서 **이름**을 선택 합니다.

8. 모든 템플릿을 변환한 다음 솔루션을 빌드하고 실행 합니다.

9. 생성 된 디자이너에서 샘플 다이어그램을 엽니다.

10. 다이어그램의 comment 요소와 **Task1** 요소 사이에 **주석 연결선** 을 그립니다.

     탐색기 노드는 주석을 **Task1**로 표시 해야 합니다.

## <a name="hiding-nodes"></a>노드 숨기기
 **DSL 탐색기**의 **숨겨진 노드** 노드에 해당 경로를 추가 하 여 탐색기에서 노드를 숨길 수 있습니다. 다음 절차에서는 **주석** 노드를 숨기는 방법을 보여 줍니다.

#### <a name="to-hide-an-explorer-node"></a>탐색기 노드를 숨기려면

1. 이전 절차에서 만든 솔루션을 엽니다.

2. **DSL 탐색기**에서 **탐색기 동작** 을 마우스 오른쪽 단추로 클릭 한 다음 **새 도메인 경로 추가**를 클릭 합니다.

     **숨겨진 노드**아래에 **도메인 경로** 노드가 나타납니다.

3. **도메인 경로**를 선택 하 고 **속성** 창에서 **경로 정의**의 값 필드를 클릭 합니다. **Flowgraph**를 선택 하 고 **Flowgraphhascomments**를 선택 합니다. 결과 경로는 **Flowgraphhascomments** 와 유사 해야 합니다. 주석

4. 모든 템플릿을 변환한 다음 솔루션을 빌드하고 실행 합니다.

5. 생성 된 디자이너에서 샘플 다이어그램을 엽니다.

     탐색기에는 **행위자** 노드만 표시 되 고 **주석** 노드는 표시 되지 않습니다.

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
