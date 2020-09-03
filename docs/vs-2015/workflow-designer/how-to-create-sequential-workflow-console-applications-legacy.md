---
title: '방법: 순차 워크플로 콘솔 응용 프로그램 만들기 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662722"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>방법: 순차 워크플로 콘솔 애플리케이션 만들기(레거시)
[!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 제공하는 레거시 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 사용하여 순차 워크플로 콘솔 애플리케이션 프로젝트를 만들려면 다음 단계를 따릅니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

### <a name="to-create-a-sequential-workflow-console-application"></a>순차 워크플로 콘솔 애플리케이션을 만들려면

1. Visual Studio를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 선택합니다.

     **새 프로젝트** 대화 상자가 열립니다.

3. **새 프로젝트** 창의 맨 위에 있는 드롭다운 목록에서 **.NET Framework 3.0** 옵션 또는 **.NET Framework 3.5** 옵션 중 하나를 선택 하 여 레거시 디자이너에 액세스 합니다.

    > [!NOTE]
    > 의 기본 옵션 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 은 **.NET Framework 4**입니다. 이 옵션은 [!INCLUDE[wf](../includes/wf-md.md)]을 대상으로 하는 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 애플리케이션을 만드는 데 사용합니다.

4. **프로젝트 형식** 창에서 Visual c # 프로젝트 또는 Visual Basic 프로젝트 ( **다른 언어**아래)를 선택 하 고 **워크플로**를 선택 합니다.

5. **템플릿** 창에서 **순차 워크플로 콘솔 응용 프로그램**을 선택 합니다.

6. **이름** 상자에 프로젝트에 대 한 설명이 포함 된 이름을 입력 하 여 쉽게 식별할 수 있도록 합니다.

7. **위치** 상자에 프로젝트를 저장할 디렉터리를 입력 하거나 **찾아보기** 를 클릭 하 여 이동 합니다.

     Windows Forms 디자이너가 열리며 사용자가 만든 프로젝트의 Form1이 나타납니다.

8. **확인**을 클릭합니다.

     워크플로 디자이너가 열리며 사용자가 만든 순차 워크플로의 워크플로 디자인 화면이 나타납니다.

9. 활동을 **도구 상자** 에서 지정 된 **Drop activity** 영역에 있는 디자인 화면으로 끕니다.

## <a name="see-also"></a>관련 항목
 [워크플로를 개발](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301) 하는 [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md)