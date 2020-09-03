---
title: '방법: 워크플로 콘솔 응용 프로그램 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604925"
---
# <a name="how-to-create-a-workflow-console-application"></a>방법: 워크플로 콘솔 애플리케이션 만들기
[!INCLUDE[wf](../includes/wf-md.md)]에서는 시스템 또는 사용자 프로세스를 실행하는 워크플로를 만들 수 있습니다. [!INCLUDE[wfd1](../includes/wfd1-md.md)]에는 이러한 워크플로를 만들 수 있는 디자인 화면이 있습니다. [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 내에서 워크플로를 만드는 데 사용되거나 디자이너를 다시 호스트하는 다른 애플리케이션에 통합될 수 있습니다.

 이 항목에서는 [!INCLUDE[wfd2](../includes/wfd2-md.md)]의 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 사용하여 콘솔 애플리케이션에 워크플로를 만드는 방법에 대해 설명합니다.

### <a name="to-create-a-workflow-console-application"></a>워크플로 콘솔 애플리케이션을 만들려면

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트 ...** 를 선택 합니다.

     **새 프로젝트** 대화 상자가 열립니다.

3. **설치 된 템플릿** 창에서 선호 하는 언어에 따라 **Visual c #** 또는 **Visual Basic** 그룹에서 **워크플로** 를 선택 합니다.

4. 가운데 창에서 **워크플로 콘솔 응용 프로그램**을 선택 합니다.

5. **이름** 상자에 프로젝트에 대 한 설명이 포함 된 이름을 입력 하 여 쉽게 식별할 수 있도록 합니다.

6. **위치** 상자에 프로젝트를 저장할 디렉터리를 입력 하거나 **찾아보기** 를 클릭 하 여 이동 합니다.

7. **솔루션** 상자에 새 솔루션의 이름을 입력 합니다. **확인** 을 클릭 하 여 응용 프로그램을 만듭니다.

    > [!NOTE]
    > 기존 솔루션에 워크플로 콘솔 응용 프로그램을 추가 하려면에서 해당 솔루션을 열고 [!INCLUDE[vs2010](../includes/vs2010-md.md)] **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 한 다음 **추가**, **새 프로젝트** ...를 차례로 선택 합니다. **새 프로젝트** 대화 상자를 엽니다. 그런 다음 이 절차의 윗부분에 설명된 대로 진행합니다.

8. 프로젝트 템플릿이 XAML로 워크플로 정의를 만들고 소스 코드 안에 콘솔 애플리케이션 정의를 만듭니다. [!INCLUDE[wfd2](../includes/wfd2-md.md)]가 열리고 만들어진 워크플로의 캔버스가 표시됩니다.

9. 워크플로를 작성 하려면 **도구 상자** 에서 워크플로의 디자인 화면으로 활동 또는 다른 워크플로 항목을 끌어 옵니다.

## <a name="see-also"></a>관련 항목
 [워크플로 프로젝트 만들기](../workflow-designer/creating-a-workflow-project.md)