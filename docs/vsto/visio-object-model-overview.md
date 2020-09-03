---
title: Visio 개체 모델 개요
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88695511d22e38262dc969d66e469441c9c3ac47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985476"
---
# <a name="visio-object-model-overview"></a>Visio 개체 모델 개요
  Microsoft Office Visio용 Office 솔루션을 개발하기 위해 Visio 개체 모델을 조작할 수 있습니다. 이 개체 모델은 Visio용 주 interop 어셈블리에 제공되고 `Microsoft.Office.Interop.Visio` 네임스페이스에서 제공되는 클래스 및 인터페이스로 구성됩니다.

 이 항목에서는 Visio 개체 모델에 대해 간략하게 설명합니다. Visio 개체 모델을 사용하여 Office 프로젝트에서 작업을 수행하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.

- [Visio 문서 작업](../vsto/working-with-visio-documents.md)

- [Visio 셰이프 작업](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Visio 개체 모델 이해
 Visio는 조작할 수 많은 개체를 제공합니다. 이러한 개체는 사용자 인터페이스와 유사한 계층 구조로 구성됩니다. 계층 구조의 맨 위에는 [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) 개체가 있습니다. 이 개체는 Visio의 현재 인스턴스를 나타냅니다. 개체는 및 `Microsoft.Office.Interop.Visio.Application` `Microsoft.Office.Interop.Visio.Document` 개체와 `Microsoft.Office.Interop.Visio.Page` `Microsoft.Office.Interop.Visio.Documents` 및 컬렉션을 포함 합니다 `Microsoft.Office.Interop.Visio.Pages` . 이러한 각 개체 및 컬렉션에는 조작하고 상호 작용하기 위해 액세스할 수 있는 여러 메서드와 속성이 있습니다.

 자세한 내용은 [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)및 [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) 개체와 [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) 및 [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) 컬렉션에 대한 VBA 참조 설명서를 참조하세요.

 다음 섹션에서는 최상위 개체 및 최상위 개체가 서로 상호 작용하는 방식을 간략하게 설명합니다. 이러한 개체에는 다음 개체가 포함됩니다.

- 애플리케이션 개체

- Document 개체

- Page 개체

### <a name="application-object"></a>애플리케이션 개체
 Microsoft 응용 프로그램은 Visio 응용 프로그램을 나타내며 다른 모든 개체의 부모입니다. 멤버는 일반적으로 전체 Visio에 적용됩니다. Microsoft 응용 프로그램과 개체의 속성 및 메서드 `Microsoft.Office.Interop.Visio.ApplicationSettings` 를 사용 하 여 Visio 환경을 제어할 수 있습니다.

 VSTO 추가 기능 프로젝트에서 `Application` 클래스의 필드를 사용 하 여 Microsoft 응용 프로그램 개체에 액세스할 수 있습니다. `ThisAddIn` 자세한 내용은 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)을 참조하세요.

### <a name="document-object"></a>Document 개체
 Microsoft.Office.Interop.Visio.Document 개체는 Visio 프로그래밍의 핵심입니다. 드로잉, 스텐실 또는 템플릿 파일을 나타냅니다. Visio 문서를 열거나 새 문서를 만드는 경우 ument 개체의 Microsoft.Office.Interop.Visio.Documents 컬렉션에 추가 되는 새 Microsoft.Office.Interop.Visio.Doc개체를 만듭니다 .이 개체는

 포커스가 있는 문서를 활성 문서라고 합니다. 이 클래스는 `Microsoft.Office.Interop.Visio.Application.ActiveDocument` Microsoft의 속성으로 표시 됩니다.

### <a name="page-object"></a>Page 개체
 Microsoft.. m a. m. m. 페이지 개체는 전경 페이지나 배경 페이지의 그리기 영역을 나타냅니다. `Microsoft.Office.Interop.Visio.Page.Background` 속성을 사용하여 페이지가 전경 또는 배경 페이지인지 결정합니다.

 셰이프를 만들려면 `Microsoft.Office.Interop.Visio.Page.DrawSpline` 및 `Microsoft.Office.Interop.Visio.Page.DrawOval` 메서드를 포함하는 메서드를 사용할 수 있습니다. 또한 스텐실에서 마스터를 검색하고 `Microsoft.Office.Interop.Visio.Page.Drop` 또는 `Microsoft.Office.Interop.Visio.Page.DropMany` 메서드를 사용하여 페이지에 셰이프를 배치할 수 있습니다.

## <a name="use-the-visio-object-model-documentation"></a>Visio 개체 모델 설명서 사용
 Visio 개체 모델에 대한 자세한 내용은 Visio VBA 개체 모델 참조를 참조하세요. VBA 개체 모델 참조에서는 VBA(Visual Basic for Applications) 코드로 표시되는 Visio 개체 모델에 대해 설명합니다. 자세한 내용은 [Visio 개체 모델 참조](/office/vba/api/overview/visio/object-model)를 참조 하세요.

 VBA 개체 모델 참조의 모든 개체 및 멤버는 Visio PIA(주 interop 어셈블리)의 형식 및 멤버에 해당합니다. 예를 들어 `Document` VBA 개체 모델 참조의 개체는 VISIO PIA의 Microsoft.Office.Interop.Visio.Document 형식에 해당 합니다. VBA 개체 모델 참조에서는 대부분의 속성, 메서드 및 이벤트에 대한 코드 예제를 제공하지만 Visual Studio를 사용하여 만든 Visio VSTO 추가 기능 프로젝트에서 사용하려면 이 참조의 VBA 코드를 Visual Basic 또는 Visual C#으로 변환해야 합니다.

> [!NOTE]
> 이번에는 Visio 주 interop 어셈블리에 대한 참조 설명서가 없습니다.

 관련 된 코드 샘플과 Visio 솔루션을 만들기 위한 추가 도구는 [visio 2010 소프트웨어 개발 키트](https://www.microsoft.com/download/details.aspx?id=12365)를 참조 하세요.

### <a name="additional-types-in-primary-interop-assemblies"></a>주 interop 어셈블리의 추가 형식
 구현 차이 때문에 VBA에 표시되지 않는 형식을 주 interop 어셈블리에서 찾을 수 있습니다. VBA는 직접 사용할 수 있는 개체와 멤버만 포함하는 Visio 개체 모델의 뷰를 제공합니다. 주 interop 어셈블리는 동일한 개체 모델을 노출하지만, COM 개체 모델의 개체를 관리 코드로 변환하는 다른 인터페이스, 클래스 및 멤버도 포함합니다. 이러한 추가 항목은 코드에서 직접 사용할 수 없습니다.

 자세한 내용은 Office 주 interop 어셈블리 및 [office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)의 [클래스 및 인터페이스 개요](/previous-versions/office/office-12/ms247299(v=office.12)) 를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Visio 솔루션](../vsto/visio-solutions.md)
- [Visio 문서 작업](../vsto/working-with-visio-documents.md)
- [Visio 셰이프 작업](../vsto/working-with-visio-shapes.md)
