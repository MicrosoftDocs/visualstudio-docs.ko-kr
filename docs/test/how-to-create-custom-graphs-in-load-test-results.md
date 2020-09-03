---
title: '방법: 부하 테스트 결과에서 사용자 지정 그래프 만들기'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1cc9c5bab7601a62bacfbbb155227bd5b632f93a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287807"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>방법: 부하 테스트 결과에서 사용자 지정 그래프 만들기

부하 테스트 결과에 대한 특정 정보를 표시하는 그래프를 디자인할 수 있습니다. 그래프에 표시할 부하 테스트 카운터를 지정하여 사용자 지정 그래프를 디자인합니다.

부하 테스트가 실행되는 동안 또는 부하 테스트의 실행이 완료된 후 다음 절차를 수행할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>사용자 지정 부하 테스트 결과 그래프를 만들려면

1. **부하 테스트** 도구 모음에서 **새 그래프 추가**를 선택합니다.

     \- 또는-

     **부하 테스트 분석기**에서 **카운터** 패널 또는 그래프를 마우스 오른쪽 단추로 클릭한 다음, **그래프 추가**를 선택합니다.

     **그래프 이름 입력** 대화 상자가 표시됩니다.

2. **그래프 이름**에 그래프의 이름을 입력하고 **확인**을 선택합니다.

     새 그래프가 **부하 테스트 분석기**에 표시됩니다. 새 그래프는 현재 선택된 그래프 패널에 나타나며 이전에 해당 패널에 표시되었던 그래프를 대체합니다.

3. 카운터를 추가하여 새 그래프를 사용자 지정합니다. 자세한 내용은 [방법: 그래프에서 카운터 추가 및 삭제](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [그래프 뷰에서 부하 테스트 결과 분석](../test/analyze-load-test-results-in-the-graphs-view.md)
- [방법: 그래프에서 카운터 추가 및 삭제](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
