---
title: '방법: 순차 워크플로 라이브러리 만들기 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: adc2e71678e6892d12640a3153f24bfb90dfa429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663406"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>방법: 순차 워크플로 라이브러리 만들기(레거시)
[!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 제공하는 레거시 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 사용하여 순차 워크플로 라이브러리 프로젝트를 만들려면 다음 단계를 따릅니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

### <a name="to-create-a-sequential-workflow-library-project"></a>순차 워크플로 라이브러리 프로젝트를 만들려면

1. Visual Studio를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 선택합니다.

     **새 프로젝트** 대화 상자가 열립니다.

3. **새 프로젝트** 창의 맨 위에 있는 드롭다운 목록에서 **.NET Framework 3.0** 옵션 또는 **.NET Framework 3.5** 옵션 중 하나를 선택 하 여 레거시 디자이너에 액세스 합니다.

    > [!NOTE]
    > 의 기본 옵션 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 은 **.NET Framework 4**입니다. 이 옵션은 [!INCLUDE[wf](../includes/wf-md.md)]을 대상으로 하는 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 애플리케이션을 만드는 데 사용합니다.

4. **프로젝트 형식** 창에서 Visual c # 또는 Visual Basic ( **다른 언어**아래)를 선택한 다음 **워크플로**를 선택 합니다.

5. **템플릿** 창에서 **순차 워크플로 라이브러리**를 선택 합니다.

6. **이름** 상자에 프로젝트에 대 한 설명이 포함 된 이름을 입력 하 여 쉽게 식별할 수 있도록 합니다.

7. **위치** 상자에 프로젝트를 저장할 디렉터리를 입력 하거나 **찾아보기** 를 클릭 하 여 이동 합니다.

     프로젝트에 대해 솔루션 디렉터리를 만들려는 경우 **솔루션용 디렉터리 만들기** 확인란을 선택 하 고 **솔루션 이름** 상자에 이름을 입력 합니다.

8. **확인**을 클릭합니다.

## <a name="see-also"></a>참고 항목
 [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md) [워크플로 제작 스타일](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739)