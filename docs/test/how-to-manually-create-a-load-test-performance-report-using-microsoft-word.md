---
title: Microsoft Word를 사용하여 부하 테스트 성능 보고서 만들기
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3deee8d35f06e50dbe22001e8a2fa81b41563e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113435"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>방법: Microsoft Word를 사용하여 수동으로 부하 테스트 성능 보고서 만들기

부하 테스트 결과 요약 뷰와 그래프 뷰에서 데이터를 복사하여 붙여넣는 방법으로 Microsoft Word 부하 테스트 보고서를 수동으로 만들 수 있습니다. 요약 뷰와 그래프 뷰에 표시된 데이터는 복사 시 HTML 형식으로 적용됩니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> 테이블 뷰의 일반 텍스트와 세부 정보 뷰의 스크린 샷을 Microsoft Word에 복사할 수도 있지만 이 경우에는 데이터가 HTML 형식으로 적용되지 않으므로 추가로 서식을 지정하고 편집해야 합니다.

> [!TIP]
> 올바르게 구성된 Microsoft Excel 보고서를 자동으로 생성할 수도 있습니다. 자세한 내용은 [방법: Microsoft Excel을 사용하여 부하 테스트 성능 보고서 만들기](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)를 참조하세요.

## <a name="copy-summary-view-data"></a>요약 뷰 데이터 복사

1. 요약 뷰가 현재 표시되어 있지 않은 경우 **부하 테스트 결과**의 도구 모음에서 **요약**을 클릭합니다.

2. 요약 뷰에서 마우스 오른쪽 단추를 클릭하고 **모두 선택**을 선택합니다.

3. 요약 뷰에서 마우스 오른쪽 단추를 클릭하고 **복사**를 선택합니다. 그러면 요약 뷰 데이터가 HTML 형식으로 클립보드에 렌더링됩니다.

4. Microsoft Word의 원하는 위치에 요약 뷰 데이터를 붙여넣습니다.

5. 이제 보고 요구 사항을 충족하도록 복사한 내용을 수정하고, 서식을 지정하고, 삭제할 수 있습니다.

## <a name="copy-graph-view-data"></a>그래프 뷰 데이터 복사

1. 그래프 보기가 현재 표시되어 있지 않은 경우 **부하 테스트 결과**의 도구 모음에서 **그래프**를 선택합니다.

2. (선택 사항) 다음 그림과 같이 Microsoft Word 문서에 복사할 특정 그래프를 확대합니다. 자세한 내용은 [방법: 그래프의 영역으로 확대](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)를 참조하세요.

     ![그래프 뷰 확대/축소 컨트롤](../test/media/ltest_zoomcontrol.png)

3. Microsoft Word 문서에 복사할 그래프에서 마우스 오른쪽 단추를 클릭하고 **복사**를 선택합니다.

4. Microsoft Word의 원하는 위치에 그래프와 관련 테이블 데이터를 붙여넣습니다.

    > [!WARNING]
    > 원격 데스크톱의 그래프를 복사하여 다른 컴퓨터에 붙여넣을 경우에는 그래프와 연결된 테이블 정보만 복사되고 그래프 이미지는 복사되지 않습니다. 그래프 이미지는 복사한 이미지가 있는 컴퓨터의 임시 디렉터리에 저장되므로 두 번째 컴퓨터에서 디렉터리를 역참조할 수는 없습니다.

## <a name="see-also"></a>참고 항목

- [테스트 비교 또는 추세 분석을 위한 부하 테스트 결과 보고](../test/compare-load-test-results.md)
- [방법: Microsoft Excel을 사용하여 부하 테스트 성능 보고서 만들기](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
