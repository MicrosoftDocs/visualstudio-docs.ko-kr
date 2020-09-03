---
title: Visio 솔루션
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985503"
---
# <a name="visio-solutions"></a>Visio 솔루션
  Visual Studio에서는 Microsoft Office Visio용 VSTO 추가 기능을 만드는 데 사용할 수 있는 프로젝트 템플릿을 제공합니다. VSTO 추가 기능을 사용하여 Visio를 자동화하거나, Visio 기능을 확장하거나, Visio UI(사용자 인터페이스)를 사용자 지정할 수 있습니다.

 VSTO 추가 기능에 대 한 자세한 내용은 vsto 추가 [기능 프로그래밍 시작](../vsto/getting-started-programming-vsto-add-ins.md) 및 [Vsto 추가 기능 아키텍처](../vsto/architecture-of-vsto-add-ins.md)를 참조 하세요. Microsoft Office를 사용한 프로그래밍을 처음 접하는 경우 [Visual Studio&#41;에서 Office 개발 시작 &#40;](../vsto/getting-started-office-development-in-visual-studio.md)을 참조 하세요.

 **적용 대상:** 이 항목의 정보는 Visio 2010의 VSTO 추가 기능 프로젝트에 적용됩니다. 자세한 내용은 [Office 애플리케이션 및 프로젝트 형식에 따라 사용 가능한 기능](../vsto/features-available-by-office-application-and-project-type.md)을 참조하세요.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Visio 개체 모델을 사용 하 여 Visio 자동화
 Visio 개체 모델은 Visio를 자동화하여 조직 차트, 순서도, 프로젝트 일정, 네트워크 다이어그램, 사무실 공간 등에 대한 다이어그램을 만드는 데 사용할 수 있는 많은 클래스를 노출합니다. API를 사용하여 일반적인 작업을 수행하는 코드를 작성할 수 있습니다.

- 다이어그램에서 모양과 텍스트를 생성하고 배치합니다.

- 비즈니스 논리 및 사용자 입력에 따라 모양 동작을 관리합니다.

- 이동 및 확대/축소와 같은 다이어그램 시각화를 제어합니다.

- 애플리케이션 UI를 사용자 지정합니다.

- 외부 데이터를 Visio로 가져오고, 셰이프에 연결하고, 페이지에 그래픽으로 표시합니다.

  Visio의 개체 모델을 사용 하 여 visio [문서 작업](../vsto/working-with-visio-documents.md) 의 문서 및 셰이프 작업을 수행 하는 단계별 절차 및 코드 예제를 확인 하 고 Visio [셰이프 작업](../vsto/working-with-visio-shapes.md)을 수행할 수 있습니다.

  VSTO 추가 기능에서 Visio 개체 모델에 액세스하려면 프로젝트에서 `Application` 클래스의 `ThisAddIn` 필드를 사용합니다. `Application` 필드는 Visio의 현재 인스턴스를 나타내는 `Microsoft.Office.Interop.Visio.Application` 개체를 반환합니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

  Visio 개체 모델을 호출할 때 Visio용 PIA(주 Interop 어셈블리)에서 제공되는 형식을 사용합니다. PIA는 VSTO 추가 기능의 관리 코드와 Visio의 COM 개체 모델 간의 다리 역할을 합니다. Visio PIA의 모든 형식은 `Microsoft.Office.Interop.Visio` 네임스페이스에서 정의됩니다. 주 interop 어셈블리에 대 한 자세한 내용은 [office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) 및 [office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)를 참조 하세요.

## <a name="visio-object-model-overview"></a>Visio 개체 모델 개요
 Visio 개체 모델 참조 및 Sdk에 대 한 링크를 포함 하는 visio 개체 모델 [개요](../vsto/visio-object-model-overview.md)에서 visio 개체 모델의 개요를 찾을 수 있습니다.

## <a name="customize-the-user-interface-of-visio"></a>Visio의 사용자 인터페이스 사용자 지정
 Visio UI에는 다음과 같은 사용자 지정 옵션이 있습니다.

|Task|참조 항목|
|----------|--------------------------|
|리본 메뉴 사용자 지정|[리본 개요](../vsto/ribbon-overview.md)|

 Visio UI를 사용자 지정하는 방법에 대한 자세한 내용은 [Visio.UIObject](/office/vba/api/Visio.UIObject) 클래스에 대한 VBA 참조 설명서를 참조하세요.

## <a name="see-also"></a>추가 정보
- [VSTO 추가 기능 프로그래밍 시작](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
- [Office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)
- [Office 개발에서 Visio 2010](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
