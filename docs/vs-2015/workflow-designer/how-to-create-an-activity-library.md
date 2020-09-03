---
title: '방법: 활동 라이브러리 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662751"
---
# <a name="how-to-create-an-activity-library"></a>방법: 활동 라이브러리 만들기
사용자 지정 활동은 워크플로의 특정 비즈니스 프로세스를 모델링하는 데 사용됩니다. [!INCLUDE[vs2010](../includes/vs2010-md.md)]의 활동 라이브러리 템플릿은 [!INCLUDE[wfd1](../includes/wfd1-md.md)]를 사용하여 이러한 사용자 지정 활동을 시각적으로 만들 수 있도록 하기 위한 것입니다.

### <a name="to-create-a-workflow-activity-library"></a>워크플로 활동 라이브러리를 만들려면

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트 ...** 를 선택 합니다.

     **새 프로젝트** 대화 상자가 열립니다.

3. **프로젝트 형식** 창에서 **Visual c #** 프로젝트 또는 언어 기본 설정에 따라 그룹화 **Visual Basic** 에서 **워크플로** 를 선택 합니다.

4. **템플릿** 창에서 **활동 라이브러리**를 선택 합니다.

5. **이름** 상자에 프로젝트에 대 한 설명이 포함 된 이름을 입력 하 여 쉽게 식별할 수 있도록 합니다.

6. **위치** 상자에 프로젝트를 저장할 디렉터리를 입력 하거나 **찾아보기** 를 클릭 하 여 이동 합니다.

7. **솔루션** 상자에서 솔루션에 대 한 설명이 포함 된 이름을 입력 하 고 **확인**을 클릭 합니다.

    > [!NOTE]
    > 기존 솔루션에 워크플로 콘솔 응용 프로그램을 추가 하려면에서 해당 솔루션을 열고 [!INCLUDE[vs2010](../includes/vs2010-md.md)] **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 한 다음 **추가**, **새 프로젝트** ...를 차례로 선택 합니다. **새 프로젝트** 대화 상자를 엽니다. 그런 다음 이 절차의 윗부분에 설명된 대로 진행합니다.

8. 프로젝트 템플릿이 활동 정의를 XAML로 만듭니다. [!INCLUDE[wfd1](../includes/wfd1-md.md)]가 열리고 사용자 지정 활동의 캔버스가 표시됩니다.

9. 활동을 **도구 상자** 에서 디자인 화면으로 끌어 사용자 지정 활동에 포함 합니다.

    > [!CAUTION]
    > 사용자 지정 활동의 본문에 자식 활동을 한 개만 넣을 수 있지만, 자식 활동으로 <xref:System.Activities.Statements.Sequence> 활동 또는 <xref:System.Activities.Statements.Flowchart> 활동과 같은 복합 활동을 사용할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [방법:](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [워크플로 프로젝트를 만드는](../workflow-designer/creating-a-workflow-project.md) 작업 만들기