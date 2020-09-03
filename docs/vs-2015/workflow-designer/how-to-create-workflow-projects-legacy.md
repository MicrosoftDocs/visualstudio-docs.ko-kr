---
title: '방법: 워크플로 프로젝트 만들기 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668670"
---
# <a name="how-to-create-workflow-projects-legacy"></a>방법: 워크플로 프로젝트 만들기(레거시)
[!INCLUDE[wf](../includes/wf-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 프로젝트를 만들려면 다음 단계를 따릅니다. 이 절차에서는 [!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 제공하는 레거시 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 사용합니다.

### <a name="to-create-a-workflow-project"></a>워크플로 프로젝트를 만들려면

1. [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 선택합니다.

     **새 프로젝트** 대화 상자가 열립니다.

3. **새 프로젝트** 창의 맨 위에 있는 드롭다운 목록에서 **.NET Framework 3.0** 옵션 또는 **.NET Framework 3.5** 옵션 중 하나를 선택 하 여 레거시 디자이너에 액세스 합니다.

    > [!NOTE]
    > 의 기본 옵션 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 은 **.NET Framework 4**입니다. 이 옵션은 [!INCLUDE[wf](../includes/wf-md.md)]을 대상으로 하는 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 애플리케이션을 만드는 데 사용합니다.

4. **프로젝트 형식** 창에서 Visual c # 프로젝트 또는 Visual Basic 프로젝트를 선택한 다음 **워크플로**를 선택 합니다.

5. **템플릿** 창에서 설치 된 프로젝트 템플릿 중 하나를 선택 합니다.

    - 순차 워크플로 콘솔 애플리케이션

    - 순차 워크플로 라이브러리

    - 워크플로 활동 라이브러리

    - 상태 시스템 워크플로 콘솔 애플리케이션

    - 상태 시스템 워크플로 라이브러리

    - 빈 워크플로 프로젝트

6. **이름** 상자에 프로젝트에 대 한 설명이 포함 된 이름을 입력 하 여 쉽게 식별할 수 있도록 합니다.

7. **위치** 상자에 프로젝트를 저장할 디렉터리를 입력 하거나 **찾아보기** 를 클릭 하 여 디렉터리로 이동 합니다.

     프로젝트에 대해 솔루션 디렉터리를 만들려는 경우 **솔루션용 디렉터리 만들기** 확인란을 선택 하 고 **솔루션 이름** 상자에 이름을 입력 합니다.

8. **확인**을 클릭합니다.

## <a name="see-also"></a>참고 항목
 [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md)