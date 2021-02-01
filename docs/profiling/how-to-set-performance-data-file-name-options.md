---
title: 성능 데이터 파일 이름 옵션 설정 | Microsoft Docs
description: 성능 세션에 대한 속성 대화 상자의 일반 페이지에서 명명 매개 변수를 변경하는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6dce666121214bef7d844bae2735a284589463ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722050"
---
# <a name="how-to-set-performance-data-file-name-options"></a>방법: 성능 데이터 파일 이름 옵션 설정

기본적으로 다음 구문을 사용하여 프로파일링 데이터 파일(.*vsp*)을 저장합니다.

*Path\VSP-File\YYMMDD(N)* **.vsp**

성능 세션에 대한 [속성] 대화 상자의 **일반** 페이지에서 명명 매개 변수를 변경할 수 있습니다.

|매개 변수|설명|
|-|-|
|*경로*|보고서가 포함된 디렉터리입니다. 기본 위치는 사용자의 프로젝트 및 솔루션에 대한 솔루션 폴더 또는 기본 위치입니다.|
|*VSP-File*|프로파일링 데이터 파일의 이름입니다. 기본 이름은 프로파일링되는 솔루션 또는 실행 파일의 이름입니다.|
|*YYMMDD*|프로파일링 데이터가 수집된 연도, 월 및 일을 표시하는 날짜 스탬프입니다.|
|*(N)*|두 개 이상의 프로파일링 데이터 파일이 있으면 괄호 사이의 파일 이름에 증분된 숫자가 추가됩니다.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>성능 세션에 대한 프로파일링 데이터 파일의 명명 구문을 변경하려면

1. **성능 탐색기** 에서 성능 세션의 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성** 을 클릭합니다.

2. **일반** 을 클릭합니다.

3. **보고서** 에서 다음 설정을 변경합니다.

    |이름|설명|
    |-|-|
    |**보고서 위치**|프로파일링 데이터 파일을 저장할 디렉터리를 지정합니다.|
    |**보고서 이름**|파일의 기본 이름을 지정합니다.|
    |**자동으로 세션에 새 보고서 추가**|데이터 파일을 성능 세션에 자동으로 추가하려면 확인란을 선택합니다.|
    |**생성된 보고서에 증분 번호 추가**|같은 이름을 가진 파일이 두 개 이상 있을 경우 파일 이름에 증분 번호를 추가하려면 확인란을 선택합니다. 기존 파일을 덮어쓰려면 확인란의 선택을 취소합니다.|
    |**숫자에 타임스탬프 사용**|파일 이름에 날짜 스탬프를 추가하려면 확인란을 선택합니다.|
