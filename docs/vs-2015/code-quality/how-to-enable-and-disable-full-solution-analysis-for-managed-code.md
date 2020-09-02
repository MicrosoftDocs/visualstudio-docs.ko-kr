---
title: '방법: 관리 코드에 대 한 전체 솔루션 분석 사용 및 사용 안 함 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646287"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>방법: 관리 코드에 대한 전체 솔루션 분석 활성화 및 비활성화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 이 항목은 Visual Studio 2015 업데이트 3 RC 이상에만 적용 됩니다.

 *전체 솔루션 분석* 은 솔루션의 열려 있는 Visual c # 또는 Visual Basic 파일 또는 솔루션의 열려 있는 visual c # 또는 Visual Basic 파일 둘 다에서 코드 분석 문제가 표시 되는지 여부를 선택할 수 있는 visual Studio 기능입니다.

 모든 파일의 모든 문제를 확인 하는 것이 유용 하지만, 솔루션이 매우 크거나 파일이 많은 경우 Visual Studio의 속도가 저하 될 수 있습니다.  표시 되는 문제 수를 제한 하 고 Visual Studio 성능을 향상 시키려면 전체 솔루션 분석을 사용 하지 않도록 설정할 수 있습니다. 원할 경우이 기능을 쉽게 다시 활성화할 수 있습니다.

#### <a name="to-toggle-full-solution-analysis"></a>전체 솔루션 분석을 설정/해제 하려면

1. Visual Studio의 주 메뉴에서 **도구** &#124; **옵션** 을 선택 하 여 **옵션** 대화 상자를 표시 합니다.

2. **옵션** 대화 상자에서 **텍스트 편집기** &#124; **c #** 또는 **Basic** &#124; **고급**을 선택 합니다.

3. 전체 솔루션 분석 **사용** 확인란을 선택 하 여 전체 솔루션 분석을 사용 하도록 설정 하거나 확인란의 선택을 취소 하 여 사용 하지 않도록 설정 합니다. 완료 되 면 **확인** 단추를 선택 합니다.

     ![전체 솔루션 분석 사용 확인란을 선택 합니다.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>전체 솔루션 분석을 사용 및 사용 하지 않도록 설정 하는 결과
 다음 스크린샷에서 전체 솔루션 분석을 사용 하도록 설정 하면 결과를 볼 수 있습니다. 솔루션에 있는 *모든* 파일의 모든 오류 및 코드 분석 문제는 파일이 열려 있는지 여부에 관계 없이 표시 됩니다.

 ![전체 솔루션 분석을 사용 하도록 설정 했습니다.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 다음 스크린샷은 전체 솔루션 분석을 사용 하지 않도록 설정한 후 동일한 솔루션의 결과를 보여 줍니다. 열려 있는 솔루션 파일의 오류 및 코드 분석 문제도 오류 목록에 표시 됩니다.

 ![전체 솔루션 분석을 사용 하지 않습니다.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>자동으로 전체 솔루션 분석 사용 안 함
 Visual Studio에서 200MB 이하의 시스템 메모리를 사용할 수 있음을 감지 하면 사용 하도록 설정 된 경우 일부 다른 기능 뿐만 아니라 전체 솔루션 분석을 자동으로 비활성화 합니다. 이 문제가 발생 하면이를 알리는 경고가 표시 됩니다. 이 작업을 수행 하려면 단추를 사용 하 여 전체 솔루션 분석을 다시 활성화할 수 있습니다.

 ![경고 텍스트 전체 솔루션 분석 일시 중단](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>추가 정보
 기본적으로 전체 솔루션 분석은 Visual Basic에 대해 사용 하도록 설정 되 고 Visual c #에서는 사용 하지 않도록 설정 됩니다.

 Visual Studio 업데이트 3 RC에는 전체 솔루션 분석을 사용 하도록 설정한 경우에도 메모리 사용을 크게 줄이고 CPU 시간을 유휴 상태로 낮추는 향상 된 코드 분석기 진단 v2 엔진이 포함 되어 있습니다.
