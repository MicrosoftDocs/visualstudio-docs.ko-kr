---
title: 관리 코드에 대한 전체 솔루션 분석을 & 비활성화
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428190"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>방법: 관리 코드에 대한 전체 솔루션 분석 사용 및 비활성화

*전체 솔루션 분석은* 코드 분석이 편집기에서 열려 있는지 여부에 관계없이 솔루션의 모든 C# 또는 Visual Basic 파일을 검사한다는 것을 의미합니다. 기본적으로 전체 솔루션 분석은 Visual Basic에 대해 *활성화되고* C#에 대해 *비활성화됩니다.*

모든 파일의 모든 문제를 확인하는 것이 유용할 수 있지만 주의를 분산시킬 수도 있습니다. 솔루션이 매우 크거나 파일이 많은 경우 Visual Studio 속도가 느려집니다. 표시된 문제 수를 제한하고 Visual Studio 성능을 향상하려면 전체 솔루션 분석을 사용하지 않도록 설정할 수 있습니다. 필요한 경우 이 기능을 쉽게 다시 사용할 수 있습니다.

다음 이미지에서는 전체 솔루션 분석이 활성화됩니다. 솔루션의 모든 파일에서 컴파일러 및 코드 분석 문제가 열려 있지 않더라도 표시됩니다.

![전체 솔루션 분석이 활성화되었습니다.](../code-quality/media/fsa_enabled.png)

다음 이미지는 전체 솔루션 분석을 사용하지 않도록 설정한 후 동일한 솔루션의 결과를 보여 주며, 이러한 결과를 보여 주어 도있습니다. 열린 솔루션 파일의 컴파일러 오류 및 코드 분석 문제만 오류 목록에 나타납니다.

![전체 솔루션 분석을 사용할 수 없습니다.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>전체 솔루션 분석 전환

1. **옵션** 대화 상자를 열려면 Visual Studio의 메뉴 모음에서 **도구** > **옵션을 선택합니다.**

1. **옵션** 대화 상자에서 **텍스트 편집기** > **C#** 또는 **기본** > **고급**을 선택합니다.

1. 전체 **솔루션 분석 활성화** 확인란을 선택하여 전체 솔루션 분석을 활성화하거나 상자를 선택 취소하여 비활성화합니다. 작업이 완료되면 **확인을** 선택합니다.

   ![전체 솔루션 분석 확인란을 활성화합니다.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>전체 솔루션 분석을 자동으로 비활성화

Visual Studio에서 200MB 이하의 시스템 메모리를 사용할 수 있음을 감지하면 전체 솔루션 분석(및 기타 기능)이 활성화된 경우 자동으로 비활성화됩니다. 이 경우 Visual Studio에서 일부 기능을 비활성화했다는 경고가 나타납니다. 원할 경우 단추를 사용하면 전체 솔루션 분석을 다시 사용할 수 있습니다.

![전체 솔루션 분석을 일시 중단하는 경고 텍스트](../code-quality/media/fsa_alert.png)
