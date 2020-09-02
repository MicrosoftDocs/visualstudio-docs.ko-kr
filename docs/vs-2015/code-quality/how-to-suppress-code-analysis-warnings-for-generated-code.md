---
title: '방법: 생성 된 코드에 대 한 코드 분석 경고 표시 안 함 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646269"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>방법: 생성된 코드에 대한 코드 분석 경고 표시 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관리 코드 컴파일러는 코드를 신속 하 게 개발 하기 위해 프로젝트에 추가 되는 코드를 생성 하는 경우가 많습니다. 또한 개발자는 종종 타사 도구를 사용 하 여 응용 프로그램을 신속 하 게 개발할 수 있습니다. 이러한 도구는 또한 프로젝트에 추가 되는 코드를 생성 합니다.

 코드 분석이 생성 된 코드에서 검색 하는 규칙 위반을 확인 하는 것이 좋습니다. 그러나 위반을 포함 하는 코드를 보고 유지 관리할 수 없는 경우에는이를 확인 하지 않을 수 있습니다.

 프로젝트의 코드 분석 속성 페이지에서 **생성 된 코드에서 결과 표시 안 함** 확인란을 사용 하면 타사 도구에 의해 생성 된 코드에서 코드 분석 경고를 표시할지 여부를 선택할 수 있습니다.

> [!NOTE]
> 이 옵션은 폼 및 템플릿에 오류 및 경고가 표시 될 때 생성 된 코드의 코드 분석 오류 및 경고를 표시 하지 않습니다. 폼이나 템플릿의 소스 코드를 볼 수도 있고 유지 관리할 수도 있습니다.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>프로젝트에서 생성 된 코드에 대 한 경고를 표시 하지 않으려면

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

2. **코드 분석**을 클릭합니다.

3. 생성 된 **코드에서 결과 표시 안 함** 확인란을 선택 합니다.
