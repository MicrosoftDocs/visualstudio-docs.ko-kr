---
title: '방법: 보고서 뷰에서 노이즈 감소 구성 | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ccfb9dab504bc3fa9405bb56c9fce82ed18820ac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776334"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>방법: 보고서 뷰에서 노이즈 감소 구성
호출 트리 뷰 및 할당 뷰에 제공되는 데이터 양을 제한하여 노이즈 감소를 위한 성능 보고서를 구성할 수 있습니다. 노이즈 감소를 사용하면 성능 문제가 더 두드러집니다. 성능 보고서를 분석할 경우 이 방법이 유용합니다.

 노이즈 감소 구성 옵션에는 다음 설정이 포함됩니다.

- **잘라내기** 보고서가 분석될 때 뷰에서는 이어서 나오는 잘라내기 절차에 설명된 대로 구성한 값 및 임계값 설정에 해당하는 함수를 생략합니다. 기본적으로 잘라내기는 사용하도록 설정됩니다.

- **접기** 접기를 사용하도록 설정하면 이어서 나오는 접기 절차에 설명된 대로 구성한 설정을 충족하는 경로의 연속 함수가 병합됩니다. 기본적으로 접기는 사용하도록 설정됩니다.

### <a name="to-configure-trimming-for-a-performance-report"></a>성능 보고서에 대한 잘라내기를 구성하려면

1. 생성된 보고서에서 호출 트리 뷰 또는 할당 뷰가 표시되면 **개발자** 메뉴에서 **프로파일러**, **노이즈 감소 옵션**을 차례로 클릭합니다.

     **노이즈 감소** 대화 상자가 나타납니다.

2. 잘라내기를 사용하도록 설정하려면 다음 단계를 수행합니다.

    1. **잘라내기 사용**을 선택합니다. 이 값은 기본 설정입니다.

        > [!NOTE]
        > 노이즈 감소가 사용되면 알림 표시줄이 보고서에 표시됩니다. 자세한 내용은 [호출 트리 뷰](../profiling/call-tree-view.md) 및 [할당 뷰](../profiling/dotnet-memory-allocations-view.md)를 참조하세요.

    2. **값** 드롭다운 목록을 사용하고 적용 가능한 설정을 선택하여 값 설정을 구성합니다.

    3. **임계값** 텍스트 상자에 백분율 값을 입력하여 원하는 임계값 설정을 구성합니다.

    4. 생성된 보고서에서 노이즈 감소 경고를 사용하도록 설정하려면 **노이즈 감소를 사용하도록 설정한 경우 경고를 표시합니다.** 를 선택합니다. 이 값은 기본 설정입니다.

3. 잘라내기를 사용하지 않도록 설정하려면 **잘라내기 사용**을 선택 취소합니다.

4. **확인**을 클릭합니다.

### <a name="to-configure-folding-for-a-performance-report"></a>성능 보고서에 대한 접기를 구성하려면

1. **개발자** 메뉴에서 **프로파일러**, **노이즈 감소 옵션**을 차례로 클릭합니다.

     **노이즈 감소** 대화 상자가 나타납니다.

2. 접기를 사용하도록 설정하려면 다음 단계를 수행합니다.

    1. **접기 사용**을 선택합니다. 이 값은 기본 설정입니다.

        > [!NOTE]
        > 노이즈 감소가 사용되면 알림 표시줄이 보고서에 표시됩니다. 자세한 내용은 [호출 트리 뷰](../profiling/call-tree-view.md) 및 [할당 뷰](../profiling/dotnet-memory-allocations-view.md)를 참조하세요.

    2. **값** 드롭다운 목록을 사용하고 적용 가능한 설정을 선택하여 값 설정을 구성합니다.

    3. **임계값** 텍스트 상자에 백분율 값을 입력하여 원하는 임계값 설정을 구성합니다.

    4. 생성된 보고서에서 노이즈 감소 경고를 사용하도록 설정하려면 **노이즈 감소를 사용하도록 설정한 경우 경고를 표시합니다.** 를 선택합니다. 이 값은 기본 설정입니다.

3. 접기를 사용하지 않도록 설정하려면 **접기 사용**을 선택 취소합니다.

4. **확인**을 클릭합니다.

## <a name="see-also"></a>참고 항목
- [성능 도구 보고서 뷰 사용자 지정](../profiling/customizing-performance-tools-report-views.md)
- [방법: 계측에서 간단한 함수 제외 또는 포함](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [호출 트리 뷰](../profiling/call-tree-view.md)
- [할당 뷰](../profiling/dotnet-memory-allocations-view.md)
