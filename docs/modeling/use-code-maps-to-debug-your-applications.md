---
title: 코드 맵을 사용하여 애플리케이션 디버그
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e01857878f927c619529d3bbfc63728f84f0b81d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594112"
---
# <a name="use-code-maps-to-debug-your-applications"></a>코드 맵을 사용하여 애플리케이션 디버그

코드 맵을 사용하면 많은 코드베이스, 익숙하지 않은 코드 또는 레거시 코드에서 길을 잃는 것을 방지할 수 있습니다. 예를 들어, 디버깅 하는 경우 여러 파일 및 프로젝트에서 코드를 확인 해야 할 수 있습니다. 코드 맵을 사용하여 코드를 탐색하고 코드 조각 간의 관계를 확인할 수 있습니다. 이렇게 하면 머릿속에서 이 코드를 추적하거나 별도 다이어그램을 그리지 않아도 됩니다. 따라서 작업이 중단된 경우 코드 맵을 통해 작업 중인 코드에 대한 기억을 상기시킬 수 있습니다.

![코드 맵 &#45; 코드 맵 관계](../modeling/media/codemapstoryboardpaint.png)

**편집기에서 커서가 표시 되는 위치를 보여 주는 녹색 화살표**

코드 맵으로 작업할 때 사용할 수 있는 명령 및 작업에 대 한 자세한 내용은 [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)을 참조 하세요.

> [!NOTE]
> 코드 맵을 만들고 편집 하려면 Visual Studio Enterprise 버전이 필요 합니다. Visual Studio Community 및 Professional 버전에서는 Enterprise edition에서 생성 된 다이어그램을 열 수 있지만 편집할 수는 없습니다.

## <a name="understand-the-problem"></a>문제 이해
 작업 중인 드로잉 프로그램에 버그가 있다고 가정합니다. 버그를 재현 하려면 Visual Studio에서 솔루션을 열고 **F5** 키를 눌러 디버깅을 시작 합니다.

 선을 그릴 때 **마지막 스트로크 실행 취소**를 선택 하면 다음 줄을 그릴 때까지 아무 일도 발생 하지 않습니다.

 ![코드 맵 &#45; 재현 버그](../modeling/media/codemapstoryboardpaint0.png)

 따라서 `Undo` 메서드를 검색하여 조사를 시작합니다. `PaintCanvas` 클래스에서 찾습니다.

 ![코드 맵 &#45; 코드 찾기](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>코드 매핑 시작
 이제 `undo` 메서드 및 관계 매핑을 시작합니다. 코드 편집기에서 새 코드 맵을 참조하는 `undo` 메서드와 필드를 추가합니다. 새 맵을 만들 경우 코드를 인덱싱하는 데 약간의 시간이 걸립니다. 이렇게 하면 이후 작업 실행이 빨라집니다.

 ![코드 맵 &#45; 메서드 및 관련 필드 표시](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> 녹색 강조 표시에는 맵에 마지막으로 추가된 항목이 표시됩니다. 녹색 화살표는 코드에서 커서의 위치를 보여 줍니다. 항목 사이의 화살표는 다양한 관계를 나타냅니다. 마우스로 가리키고 도구 설명을 검토하여 맵에서 항목에 대한 더 자세한 정보를 얻을 수 있습니다.

 ![코드 맵 &#45; 도구 설명 표시](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>맵에서 코드 탐색 및 검사
 각 필드에 대 한 코드 정의를 보려면 맵의 필드를 두 번 클릭 하거나 필드를 선택 하 고 **F12**키를 누릅니다. 녹색 화살표를 누르면 맵의 항목 사이에서 이동합니다. 코드 편집기의 커서를 눌러도 자동으로 이동할 수 있습니다.

 ![코드 맵 &#45; 검사 필드 정의](../modeling/media/codemapstoryboardpaint5.png)

 ![코드 맵 &#45; 검사 필드 정의](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> 코드 편집기에서 커서를 이동하여 맵의 녹색 화살표를 이동할 수도 있습니다.

## <a name="understand-relationships-between-pieces-of-code"></a>코드 조각 간의 관계 이해
 이제 `history` 및 `paintObjects` 필드와 상호 작용하는 다른 코드에 대해 알아 보려고 합니다. 이러한 필드를 참조하는 모든 메서드를 맵에 추가할 수 있습니다. 이 작업은 맵이나 코드 편집기에서 수행할 수 있습니다.

 ![코드 맵 &#45; 모든 참조 찾기](../modeling/media/codemapstoryboardpaint6.png)

 ![코드 편집기에서 코드 맵 열기](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Windows Phone 또는 Windows 스토어와 같은 여러 앱에 공유되는 프로젝트에서 항목을 추가할 경우 해당 항목은 항상 현재 활성화된 앱 프로젝트와 함께 맵에 나타납니다. 따라서 컨텍스트를 다른 앱 프로젝트로 변경하는 경우 맵의 컨텍스트도 공유 프로젝트에서 새로 추가된 항목에 대해 변경됩니다. 맵의 항목에 수행하는 작업은 동일한 컨텍스트를 공유하는 항목에만 적용됩니다.

 레이아웃을 변경하여 관계 흐름을 재정렬하고 맵을 읽기 쉽도록 만듭니다. 또한 항목을 끌어서 항목을 맵 주위로 이동할 수도 있습니다.

 ![코드 맵 &#45; 레이아웃 변경](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> **증분 레이아웃** 은 기본적으로 설정 되어 있습니다. 이 설정은 새 항목을 추가할 때 맵을 가능한 적게 다시 정렬합니다. 새 항목을 추가할 때마다 전체 맵을 다시 정렬 하려면 **증분 레이아웃**을 해제 합니다.

 ![코드 맵 &#45; 레이아웃 변경](../modeling/media/codemapstoryboardpaint7.png)

 이러한 메서드를 살펴보겠습니다. 맵에서 **맵에서 paintcanvas** 메서드를 두 번 클릭 하거나이 메서드를 선택 하 고 **F12**키를 누릅니다. 이 메서드가 빈 목록으로 `history` 및 `paintObjects`를 만드는 것을 볼 수 있습니다.

 ![코드 맵 &#45; 메서드 정의 검사](../modeling/media/codemapstoryboardpaint8.png)

 이제 같은 단계를 반복하여 `clear` 메서드 정의를 검사합니다. `clear`가 `paintObjects` 및 `history`와 함께 몇 가지 작업을 수행하는 것을 볼 수 있습니다. 그런 다음 `Repaint` 메서드를 호출합니다.

 ![코드 맵 &#45; 메서드 정의 검사](../modeling/media/codemapstoryboardpaint9.png)

 이제 `addPaintObject` 메서드 정의를 검사합니다. 또한 `history` 및 `paintObjects`도 사용하여 일부 작업을 수행합니다. `Repaint`도 호출합니다.

 ![코드 맵 &#45; 메서드 정의 검사](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>맵을 검토하여 문제 찾기
 `history` 및 `paintObjects`를 수정하는 모든 메서드가 `Repaint`를 호출하는 것 같습니다. `undo`가 동일한 필드를 수정함에도 불구하고 `Repaint` 메서드는 아직 `undo`를 호출하지 않습니다. 따라서 `Repaint`에서 `undo`를 호출하여 이 문제를 해결할 수 있다고 생각합니다.

 ![누락 된 메서드 호출을 찾는 코드 맵 &#45;](../modeling/media/codemapstoryboardpaint11.png)

 누락된 호출을 표시하는 맵이 없는 경우 특히 코드가 복잡한 경우 해당 문제는 찾기 더 어려울 수 있습니다.

## <a name="share-your-discovery-and-next-steps"></a>검색 및 다음 단계 공유
 사용자 또는 다른 작업자가 버그를 수정하기 전에 문제 해결 방법을 보여주는 맵에 메모를 만들 수 있습니다.

 ![후속 처리를 위한 주석 및 플래그 항목 &#45; 코드 맵](../modeling/media/codemapstoryboardpaint12.png)

 예를 들어 맵에 주석을 추가하고 색을 사용하여 항목에 플래그를 지정할 수 있습니다.

 ![주석 처리 및 플래그가 지정 된 항목 &#45; 코드 맵](../modeling/media/codemapstoryboardpaint12a.png)

 Microsoft Outlook이 설치되어 있으면 맵을 다른 사람에게 전자 메일로 보낼 수 있습니다. 또한 맵을 이미지 또는 다른 형식으로 내보낼 수도 있습니다.

 ![코드 맵 &#45; 공유, 내보내기, 메일](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>문제를 해결하고 수행했던 작업 표시
 이 버그를 해결하려면 `Repaint`에 대한 호출을 `undo`에 추가합니다.

 ![코드 맵 &#45; 누락 된 메서드 호출 추가](../modeling/media/codemapstoryboardpaint14.png)

 수정을 확인하려면 디버깅 세션을 다시 시작하고 버그를 재현해 봅니다. 이제 **마지막 스트로크 실행 취소** 를 선택 하 여 원하는 대로 작동 하 고 올바른 수정 사항을 확인 합니다.

 ![코드 맵 &#45; 코드 수정 확인](../modeling/media/codemapstoryboardpaint15.png)

 맵을 업데이트하여 수정 내용을 보여줄 수 있습니다.

 ![메서드 호출이 없는 업데이트 map &#45; 코드 맵](../modeling/media/codemapstoryboardpaint16.png)

 이제 맵은 **실행 취소** 와 다시 **그리기**간의 링크를 표시 합니다.

 ![메서드 호출을 사용 하 여 업데이트 된 map &#45; 코드 맵](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> 맵을 업데이트하면 맵을 만드는 데 사용한 코드 인덱스가 업데이트되었음을 나타내는 메시지가 나타날 수 있습니다. 누군가가 코드를 변경하여 맵이 현재 코드와 일치하지 않음을 의미합니다. 이 경우 맵을 업데이트할 수 없는 것은 아니지만 맵을 다시 만들어서 코드와 일치하는지 확인해야 할 수 있습니다.

 이제 조사를 완료 했습니다. 코드를 매핑하여 문제를 성공적으로 발견하고 해결했습니다. 코드 주위를 탐색하고 배운 내용을 기억하는 데 도움이 되며 문제를 해결하는 단계를 보여 주는 맵도 있습니다.

## <a name="see-also"></a>추가 정보

- [디버깅하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [코드 시각화](../modeling/visualize-code.md)
