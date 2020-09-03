---
title: '방법: 애플리케이션 아이콘 지정(Visual Basic, C#) | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670698"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>방법: 애플리케이션 아이콘 지정(Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트에 대한 `Icon` 속성은 컴파일된 애플리케이션에 대해 파일 탐색기 및 Windows 작업 표시줄에서 표시되는 아이콘 파일(.ico)을 지정합니다.

 `Icon` 속성은 **프로젝트 디자이너**의 **애플리케이션** 창에서 액세스할 수 있습니다. 이 속성에는 리소스나 콘텐츠 파일로 프로젝트에 추가된 아이콘 목록이 포함되어 있습니다.

> [!NOTE]
> 애플리케이션에 대한 아이콘 속성을 설정한 후에는 애플리케이션에서 각 **창** 또는 **폼**의 `Icon` 속성도 설정할 수 있습니다. WPF(Windows Presentation Foundation) 독립 실행형 애플리케이션의 창 아이콘에 대한 자세한 내용은 <xref:System.Windows.Window.Icon%2A>속성을 참조하세요.

### <a name="to-specify-an-application-icon"></a>애플리케이션 아이콘을 지정하려면

1. **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다.

2. 메뉴 모음에서 **프로젝트**, **속성**을 선택합니다.

3. **프로젝트 디자이너**가 나타나면 **애플리케이션** 탭을 선택합니다.

4. **(Visual Basic)****아이콘** 목록에서 아이콘 파일(.ico)을 선택합니다.

     **C #** **아이콘** 목록 근처에서 **\<Browse...>** 단추를 선택한 다음 원하는 아이콘 파일의 위치로 이동 합니다.

## <a name="see-also"></a>관련 항목
 [응용 프로그램 페이지, 프로젝트 디자이너 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [응용 프로그램 페이지, 프로젝트 디자이너 (c #)](../ide/reference/application-page-project-designer-csharp.md) [응용 프로그램 속성 관리](../ide/application-properties.md) [방법: 리소스 추가 또는 제거](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
