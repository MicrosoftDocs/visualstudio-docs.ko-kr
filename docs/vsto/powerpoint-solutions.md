---
title: PowerPoint 솔루션
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c41b2942b53c97222abf7308b6706a7cdc734df1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985664"
---
# <a name="powerpoint-solutions"></a>PowerPoint 솔루션
  Visual Studio에서는 Microsoft Office PowerPoint용 VSTO 추가 기능을 만드는 데 사용할 수 있는 프로젝트 템플릿을 제공합니다. VSTO 추가 기능을 사용하여 PowerPoint를 자동화하거나, PowerPoint 기능을 확장하거나, PowerPoint UI(사용자 인터페이스)를 사용자 지정할 수 있습니다.

 VSTO 추가 기능에 대 한 자세한 내용은 vsto 추가 [기능 프로그래밍 시작](getting-started-programming-vsto-add-ins.md) 및 [Vsto 추가 기능 아키텍처](architecture-of-vsto-add-ins.md)를 참조 하세요. Microsoft Office를 사용한 프로그래밍을 처음 접하는 경우 [Visual Studio&#41;에서 Office 개발 시작 &#40;](getting-started-office-development-in-visual-studio.md)을 참조 하세요.

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>PowerPoint 개체 모델을 사용 하 여 PowerPoint 자동화
 PowerPoint 개체 모델은 PowerPoint 자동화에 사용할 수 있는 다양한 형식을 노출합니다. 이러한 형식을 사용하여 일반적인 작업을 수행하는 코드를 작성할 수 있습니다.

- 프로그래밍 방식으로 프레젠테이션을 만들고 형식을 지정합니다.

- 프레젠테이션에 슬라이드를 추가하거나 제거합니다.

- 슬라이드에 도형을 추가하거나 변경합니다.

  VSTO 추가 기능에서 PowerPoint 개체 모델에 액세스 하려면 `Application` 프로젝트에서 클래스의 필드를 사용 `ThisAddIn` 합니다. `Application`필드는 PowerPoint의 현재 인스턴스를 나타내는 [응용 프로그램](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) 개체를 반환 합니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](programming-vsto-add-ins.md)을 참조 하세요.

  PowerPoint 개체 모델을 호출할 때 PowerPoint의 주 Interop 어셈블리에서 제공되는 형식을 사용합니다. 주 interop 어셈블리는 VSTO 추가 기능의 관리 코드와 PowerPoint의 COM 개체 모델 간의 다리 역할을 합니다. PowerPoint 주 interop 어셈블리의 모든 형식은 [Microsoft의 Microsoft](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) 네임 스페이스에 정의 되어 있습니다. 주 interop 어셈블리에 대 한 자세한 내용은 [office 솔루션 개발 개요 &#40;VSTO&#41;](office-solutions-development-overview-vsto.md) 및 [office 주 interop 어셈블리](office-primary-interop-assemblies.md)를 참조 하세요.

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> PowerPoint 개체 모델 설명서 사용
 PowerPoint 개체 모델에 대한 자세한 내용은 PowerPoint PIA(주 interop 어셈블리) 참조 및 VBA 개체 모델 참조를 참조할 수 있습니다.

### <a name="primary-interop-assembly-reference"></a>주 interop 어셈블리 참조
 PowerPoint PIA 참조 설명서에서는 PowerPoint에 대한 주 interop 어셈블리의 형식에 대해 설명합니다. 이 설명서는 다음 위치에서 사용할 수 있습니다. [PowerPoint 2010 주 interop 어셈블리 참조](office-primary-interop-assemblies.md)

 PIA의 클래스와 인터페이스 간의 차이점, PIA의 이벤트 구현 방식 등 PowerPoint PIA의 디자인에 대 한 자세한 내용은 [Office 주 interop 어셈블리의 클래스 및 인터페이스 개요](/previous-versions/office/developer/office-2010/ff759900(v=office.14))를 참조 하세요.

### <a name="vba-object-model-reference"></a>VBA 개체 모델 참조
 VBA 개체 모델 참조에서는 VBA(Visual Basic for Applications) 코드로 표시되는 PowerPoint 개체 모델에 대해 설명합니다. 자세한 내용은 [PowerPoint 2010 개체 모델 참조](/office/vba/api/overview/PowerPoint/object-model)를 참조 하세요.

 VBA 개체 모델 참조의 모든 개체 및 멤버는 PowerPoint PIA(주 interop 어셈블리)의 형식 및 멤버에 해당합니다. 예를 들어 VBA 개체 모델 참조의 프레젠테이션 개체는 PowerPoint PIA의 [프레젠테이션](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) 유형에 해당 합니다. VBA 개체 모델 참조에서는 대부분의 속성, 메서드 및 이벤트에 대한 코드 예제를 제공하지만 Visual Studio를 사용하여 만든 PowerPoint VSTO 추가 기능 프로젝트에서 사용하려면 이 참조의 VBA 코드를 Visual Basic 또는 Visual C#으로 변환해야 합니다.

## <a name="customize-the-user-interface-of-powerpoint"></a>PowerPoint의 사용자 인터페이스 사용자 지정
 다음과 같은 방법으로 PowerPoint의 UI를 수정할 수 있습니다.

|Task|참조 항목|
|----------|--------------------------|
|사용자 지정 작업창을 만듭니다.|[사용자 지정 작업 창](custom-task-panes.md)|
|리본에 사용자 지정 탭을 추가합니다.|[리본 개요](ribbon-overview.md)|
|리본의 기본 제공 탭에 사용자 지정 그룹을 추가합니다.|[방법: 기본 제공 탭 사용자 지정](how-to-customize-a-built-in-tab.md)|

 PowerPoint 및 기타 Microsoft Office 응용 프로그램의 UI를 사용자 지정 하는 방법에 대 한 자세한 내용은 [OFFICE ui 사용자 지정](office-ui-customization.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [연습: PowerPoint 용 첫 VSTO 추가 기능 만들기](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [VSTO 추가 기능 프로그래밍 시작](getting-started-programming-vsto-add-ins.md)
- [Office 솔루션 개발 개요 &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](architecture-of-vsto-add-ins.md)
- [방법: Visual Studio에서 Office 프로젝트 만들기](how-to-create-office-projects-in-visual-studio.md)
- [VSTO 추가 기능 프로그램](programming-vsto-add-ins.md)
- [Office 솔루션에서 코드 작성](writing-code-in-office-solutions.md)
- [Office 주 interop 어셈블리](office-primary-interop-assemblies.md)
- [Office UI 사용자 지정](office-ui-customization.md)
- [Office 개발의 PowerPoint 2010](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
