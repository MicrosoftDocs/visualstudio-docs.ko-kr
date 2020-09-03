---
title: '방법: 도구 상자에 활동 추가 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656616"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>방법: 도구 상자에 활동 추가(레거시)
또는를 대상으로 하는 레거시를 사용 하 여 워크플로 솔루션을 빌드할 때 [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 쉽게 액세스할 수 있도록 사용자 지정 활동을 워크플로 프로젝트에 추가 하 고 해당 디자이너를 **도구 상자** 에 배치할 수 있습니다. DLL (동적 연결 라이브러리)에서 **도구 상자** 에 직접 활동을 추가할 수도 있습니다.

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>DLL에서 도구 상자에 활동을 추가하려면

1. **Windows Workflow**에서 도구 상자 창 화면을 마우스 오른쪽 단추로 클릭 한 다음 **항목 선택**을 클릭 합니다.

2. **도구 상자 항목 선택** 대화 상자에서 **시스템-작업 구성 요소** 탭을 클릭 한 다음 창의 오른쪽 아래에서 **찾아보기** 를 클릭 합니다.

3. **도구 상자**에 추가할 사용자 지정 작업의 구현이 포함 된 파일 디렉터리에서 DLL을 선택한 다음 **열기**를 클릭 합니다.

4. **확인** 을 클릭 하 여 도구 상자에 활동 추가를 마칩니다.

## <a name="see-also"></a>관련 항목
 [레거시 활동 디자이너](../workflow-designer/using-the-legacy-activity-designer.md) [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md) 사용