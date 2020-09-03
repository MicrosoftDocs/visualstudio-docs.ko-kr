---
title: '방법: 메뉴 항목을 사용 하 여 경고 표시 안 함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610021"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>방법: 메뉴 항목을 사용하여 경고 표시 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 웹 사이트 프로젝트에서는 ISS(In source suppression)가 지원되지 않습니다.

 코드 분석 창을 사용하면 코드 분석 경고 표시를 숨길 수 있습니다. 경고 표시 숨김은 경고를 비활성화하는 것과 다릅니다. 경고를 표시 하지 않으면 위반의 특정 인스턴스에만 적용 됩니다. 동일한 경고의 다른 위반은 여전히 오류 목록 창에 보고 됩니다.

 코드 분석을 실행한 후 코드 분석 창에 표시된 하나 이상의 코드 분석 경고가 애플리케이션에 해당되지 않는 것인지 확인할 수 있습니다. 예를 들어 코드가 그대로 올바른지 확인할 수 있습니다. 또는 일부 위반이 낮은 우선 순위를 가지 며 현재 개발 주기에서 수정 되지 않을 수도 있습니다. 어떤 이유로든 코드를 검토했으며 해당 경고를 표시하지 않기로 결정했음을 팀 구성원에게 알리기 위해 경고가 상황에 적합하지 않을 수 있다는 사실을 밝히는 것이 좋습니다. ISS(In Source Suppression)는 경고가 생성되는 지점에 가깝게 표시 숨김을 설정할 수 있기 때문에 유용합니다.

 비 표시 제거를 소스 코드 또는 전역 비 표시 오류 (suppression) 파일에 표시할지 여부를 선택할 수 있습니다. 일부 비 표시는 전역 비 표시 오류 (suppression) 파일에 배치 해야 합니다. 이 경우 **In Source** 옵션은 사용할 수 없습니다.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>메뉴 항목을 사용 하 여 경고를 표시 하지 않으려면

1. **분석** 메뉴에서 **창** 을 선택한 다음 **코드 분석**을 선택 합니다.

2. **코드 분석** 창에서 경고 표시 안 함을 선택 합니다.

3. 작업을 선택한 다음 **메시지 표시 안 함**을 선택 하 고 **소스** 또는 **프로젝트 비**표시 제거 파일에서 하나를 선택 합니다.

     해당 경고가 표시되지 않고, 취소선이 그려진 상태로 경고가 코드 분석 창에 나타납니다.

> [!NOTE]
> 대상이 없는 비 표시 오류는 전역 비 표시 오류 (suppression) 파일에 표시 됩니다.
