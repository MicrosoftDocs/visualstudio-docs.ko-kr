---
title: 보고서 뷰 필터링 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: acdfe8f96d30ad881d8c9c0f0a9ff48c3353afee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779248"
---
# <a name="filter-report-views"></a>보고서 뷰 필터링
프로파일링 데이터 파일에 필터를 적용하여 성능 보고서 뷰에 표시되고 보고서 파일로 내보내는 프로파일링 데이터를 제한할 수 있습니다. 타임스탬프 값 사이의 데이터로 보고서를 제한하고, 특정 프로세스 및 스레드로 데이터를 제한할 수 있습니다. 파일에 필터를 저장한 다음 저장된 필터를 가져와서 다른 프로파일링 데이터 파일에서 필터를 만들 수 있습니다.

 요약 뷰에서 그래픽 타임라인을 사용하여 보고서를 시간 세그먼트로 제한할 수도 있습니다. [방법: 요약 타임라인에서 보고서 뷰 필터링](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)을 참조하세요.

 보고서에서 시스템 및 타사 코드를 제외하려면 [방법: 내 코드만 표시하도록 프로파일링 도구 보고서 뷰 필터링](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)을 참조하세요.

## <a name="procedures"></a>프로시저

#### <a name="to-create-a-profiler-report-filter"></a>프로파일러 보고서 필터를 만들려면

1. 성능 보고서 뷰 필터 창이 표시되지 않는 경우 성능 보고서 뷰 도구 모음의 **필터 표시**를 클릭합니다.

     성능 보고서 뷰 필터는 테이블입니다. 테이블의 각 행은 필터 절을 나타냅니다. 필터에 필요한 만큼의 절을 추가할 수 있습니다.

2. 필터에 추가하려는 각 절의 경우 행의 다음 필드에 값을 선택하거나 입력합니다.

    |필드|Description|
    |-----------|-----------------|
    |**및/또는**|이 절과 다음 절이 둘 다 true여야 결과와 일치하는 경우 **및**을 선택합니다. 이 절이나 다음 절 중 하나가 true이면 결과와 일치하는 경우 **또는**을 선택합니다.|
    |**필드**|데이터 필드의 표시된 목록에서 필터 절에서 사용할 보고서 필드를 선택합니다.|
    |**연산자**|필드와 값 간의 절에 원하는 관계를 지정하는 연산자를 선택합니다.<br /><br /> =    같음<br /><br /> <>  같지 않음<br /><br /> <    보다 작음<br /><br /> >    보다 큼<br /><br /> <=  작거나 같음<br /><br /> >=  크거나 같음|
    |**값**|찾을 값을 선택하거나 입력합니다. 필드에 대해 사용 가능한 값이 나열되는 필드도 있습니다.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>표시 보고서 뷰에서 프로파일러 보고서 필터를 만들려면

1. 성능 보고서 뷰 도구 모음의 **현재 뷰** 목록에서 **표시**를 선택합니다.

    표시 프로파일러 보고서가 표시됩니다.

2. 보고서의 시작 지점으로 사용할 ETW 또는 샘플링을 선택합니다.

3. Ctrl 키를 누른 채 보고서의 끝 지점으로 사용할 이벤트를 클릭합니다.

4. 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.

   - **표시에 대한 필터 추가**를 선택하면 표시 열을 필터 필드로 사용하는 필터 절이 만들어집니다.

   - **타임스탬프에 대한 필터 추가**를 선택하면 타임스탬프(밀리초) 열을 필터 필드로 사용하는 필터 절이 만들어집니다.

     두 옵션은 동일한 시작점과 끝점에서 현재 데이터 파일을 필터링합니다. 다른 보고서에서 사용할 필터를 내보내는 경우 두 옵션 중 하나가 더 나을 수 있습니다.

#### <a name="to-load-an-existing-filter-from-a-file"></a>파일에서 기존 필터를 로드하려면

1. 성능 보고서 뷰 도구 모음에서 **필터 가져오기**를 클릭합니다.

     **필터 로드** 대화 상자가 표시됩니다.

2. 로드할 필터(.vspf) 파일의 위치와 파일 이름을 지정합니다.

#### <a name="to-execute-a-filter"></a>필터를 실행하려면

- 성능 보고서 뷰 도구 모음에서 **필터 실행**을 클릭합니다.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>실행하는 데 시간이 너무 오래 걸리는 필터를 중지하려면

- 성능 보고서 뷰 도구 모음에서 **필터 중지**를 클릭합니다.

#### <a name="to-remove-a-filter-on-a-report-view"></a>보고서 뷰의 필터를 제거하려면

1. 성능 보고서 뷰 필터에서 절의 행을 삭제합니다.

2. 성능 보고서 뷰 도구 모음에서 **필터 실행**을 클릭합니다.

#### <a name="to-save-a-filter-to-a-file"></a>파일에 필터를 저장하려면

1. 성능 보고서 뷰 도구 모음에서 **필터 내보내기**를 클릭합니다.

     **필터 저장** 대화 상자가 표시됩니다.

2. 저장할 필터(.vspf) 파일의 위치와 파일 이름을 지정합니다.

## <a name="see-also"></a>참고 항목
- [성능 도구 보고서 뷰 사용자 지정](../profiling/customizing-performance-tools-report-views.md)
