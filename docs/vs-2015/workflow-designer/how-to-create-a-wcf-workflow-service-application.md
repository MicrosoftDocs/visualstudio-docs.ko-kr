---
title: '방법: WCF 워크플로 서비스 응용 프로그램 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72605008"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>방법: WCF 워크플로 서비스 애플리케이션 만들기
[!INCLUDE[indigo1](../includes/indigo1-md.md)] 워크플로 서비스 애플리케이션은 프로세스 경계를 넘어 클라이언트와 메시지를 주고 받는 분산 통신 서비스입니다. 서비스 측의 서비스 계약 구현은 .NET Framework 3.5의 레거시 워크플로 서비스와 비슷한 방식으로 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]에서 워크플로 활동을 통해 선언적으로 이루어집니다.

### <a name="to-create-a-wcf-workflow-service-application"></a>WCF 워크플로 서비스 애플리케이션을 만들려면

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트 ...** 를 선택 합니다.

     **새 프로젝트** 대화 상자가 열립니다.

3. **설치 된 템플릿** 창에서 선택한 언어에 따라 **Visual c #** 또는 **Visual Basic** 그룹에서 **WCF** 또는 **워크플로** 를 선택 합니다.

4. 가운데 창에서 **WCF 워크플로 서비스 응용 프로그램**을 선택 합니다.

5. **이름** 상자에 프로젝트에 대 한 설명이 포함 된 이름을 입력 하 여 쉽게 식별할 수 있도록 합니다.

6. **위치** 상자에 프로젝트를 저장할 디렉터리를 입력 하거나 **찾아보기** 를 클릭 하 여 이동 합니다.

7. **솔루션** 상자에서 새 솔루션 만들기를 선택 하 고 **확인**을 클릭 합니다.

    > [!NOTE]
    > 기존 솔루션에 워크플로 콘솔 응용 프로그램을 추가 하려면에서 해당 솔루션을 열고 [!INCLUDE[vs2010](../includes/vs2010-md.md)] **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 한 다음 **추가**, **새 프로젝트** ...를 차례로 선택 합니다. **새 프로젝트** 대화 상자를 엽니다. 그런 다음 이 절차의 윗부분에 설명된 대로 진행합니다.

8. 프로젝트 템플릿이 서비스 정의를 XAML로 만듭니다. [!INCLUDE[wfd1](../includes/wfd1-md.md)] 및 <xref:System.Activities.Statements.Sequence> 활동 집합을 포함하는 <xref:System.ServiceModel.Activities.Receive> 활동이 표시된 <xref:System.ServiceModel.Activities.SendReply>의 디자인 뷰가 열립니다.

## <a name="see-also"></a>관련 항목
 [방법:](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [워크플로 프로젝트를 만드는](../workflow-designer/creating-a-workflow-project.md) 작업 만들기