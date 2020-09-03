---
title: 문서 수준 사용자 지정의 캐시 된 데이터
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9985dd25ba62cc9c0735a8a8f4008a4c0abe0558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238350"
---
# <a name="cached-data-in-document-level-customizations"></a>문서 수준 사용자 지정의 캐시 된 데이터
  문서 수준 사용자 지정의 기본 목표는 Office 문서의 보기에서 데이터를 분리 하는 것입니다. 데이터는 숫자 및 텍스트를 포함 하 여 문서에 저장 된 정보를 나타냅니다. 보기는 Microsoft Office Word 및 Microsoft Office Excel의 사용자 인터페이스와 개체 모델을 나타냅니다.

 Visual Studio는 데이터 *를 데이터* *캐시로*포함 시킬 수 있도록 하 여 문서 수준 사용자 지정에서 뷰의 데이터를 분리 합니다. Word 또는 Excel을 시작 하지 않고 데이터를 직접 읽거나 수정할 수 있습니다. 이 기능은 Microsoft Office 설치 되지 않은 서버에서 문서의 데이터를 수정 해야 하는 경우에 유용 합니다. Word 및 Excel은 클라이언트 환경에서 사용 하기 위한 것입니다. 서버에서 실행 되도록 설계 되지 않았습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 문서 수준 사용자 지정에 대 한 자세한 내용은 [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) 및 [문서 수준 사용자 지정 아키텍처](../vsto/architecture-of-document-level-customizations.md)를 참조 하세요.

## <a name="understand-the-cached-data-programming-model"></a>캐시 된 데이터 프로그래밍 모델 이해
 데이터 아일랜드는 특정 요구 사항을 충족 하는 솔루션의 모든 개체를 포함할 수 있습니다. 이러한 개체에는 <xref:System.Data.DataSet> 개체, <xref:System.Data.DataTable> 개체 및 클래스에 의해 serialize 될 수 있는 다른 모든 개체가 포함 됩니다 <xref:System.Xml.Serialization.XmlSerializer> . 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.

 캐시 된 데이터에 대 한 뷰를 제공 하기 위해 문서의 컨트롤 및 *호스트 컨트롤* 을 데이터 아일랜드의 개체에 Windows Forms 바인딩할 수 있습니다. 데이터 아일랜드와 데이터 바인딩된 컨트롤 간의 데이터 바인딩은 두 개의 동기화 된 데이터를 유지 합니다. 컨트롤에 독립적인 데이터에 유효성 검사 코드를 추가할 수도 있습니다. 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

 호스트 컨트롤은 Excel 및 Word 개체 모델에서 확장 된 버전의 네이티브 개체입니다. 네이티브 개체와 달리 호스트 컨트롤은 관리 되는 데이터 개체에 직접 바인딩할 수 있습니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md) 및 [Office 문서에서 컨트롤 Windows Forms 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)를 참조 하세요.

## <a name="access-cached-data-on-the-server"></a>서버에서 캐시 된 데이터 액세스
 문서의 캐시 된 데이터에 액세스 하려면 클래스를 사용할 수 있습니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> . 이 클래스는의 일부 이며 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Excel 또는 Word를 실행 하지 않고 서버에서 사용할 수 있습니다. 캐시 된 데이터를 수정한 후 사용자가 문서를 열면 데이터에 바인딩된 모든 컨트롤이 변경 내용에 자동으로 동기화 되 고 사용자에 게 업데이트 된 데이터가 표시 됩니다. 자세한 내용은 [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)를 참조 하세요.

 Excel 및 Word는 서버의 데이터에 쓸 필요는 없으며, 클라이언트 에서만 볼 수 있습니다. Excel 및 Word를 서버에 설치 하지 않아도 됩니다. 이를 통해 향상 된 확장성 및 데이터 아일랜드를 포함 하는 문서를 빠르게 일괄 처리 하는 기능을 제공 합니다.

## <a name="data-caching-for-offline-use"></a>오프 라인에서 사용 하기 위한 데이터 캐싱
 데이터 아일랜드에 데이터를 저장 하면 오프 라인 시나리오를 사용할 수 있습니다. 사용자가 처음으로 문서를 열거나 서버에서 문서를 요청 하는 경우 데이터 아일랜드는 최신 데이터로 채워집니다. 데이터 아일랜드는 문서에 캐시 된 다음 오프 라인으로 사용할 수 있습니다. 사용할 수 있는 라이브 연결이 없더라도 사용자 (및 코드)는 데이터를 조작할 수 있습니다. 사용자가 다시 연결 하면 데이터에 대 한 변경 내용을 서버 데이터 원본에 다시 전파할 수 있습니다.

## <a name="cached-data-and-custom-xml-parts-compared"></a>캐시 된 데이터 및 사용자 지정 XML 부분 비교
 사용자 지정 XML 부분은 문서에 임의의 XML 조각을 저장 하는 방법으로 2007 Microsoft Office 시스템에서 도입 되었습니다. 사용자 지정 XML 부분이 데이터 캐시와 동일한 여러 시나리오에서 유용 하지만 데이터 아일랜드와 사용자 지정 XML 부분 간에는 약간의 차이가 있습니다. 사용자 지정 XML 부분에 대 한 자세한 내용은 [사용자 지정 xml 부분 개요](../vsto/custom-xml-parts-overview.md)를 참조 하세요.

 다음 표에서는 몇 가지 차이점과 유사성을 보여 줍니다.

|질문/특징|데이터 캐시|사용자 지정 XML 부분|
|-|----------------|----------------------|
|사용할 수 있는 Office 응용 프로그램은 무엇 인가요?|다음 응용 프로그램에 대 한 문서 수준 사용자 지정:<br /><br /> -Excel<br />-Word|다음 응용 프로그램에 대 한 문서 수준 및 응용 프로그램 수준 솔루션:<br /><br /> -Excel<br />-PowerPoint<br />-Word|
|어떤 유형의 데이터를 저장할 수 있나요?|특정 요구 사항을 충족 하는 사용자 지정 어셈블리의 모든 public 개체입니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.|모든 XML 데이터입니다.|
|Microsoft Office 응용 프로그램을 시작 하지 않고 데이터에 액세스할 수 있나요?|예,에서 제공 하는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 클래스를 사용 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 합니다.|예. <xref:System.IO.Packaging> 네임 스페이스의 클래스를 사용 하거나 OPEN XML 형식 SDK를 사용 하 여 사용 합니다.|

## <a name="see-also"></a>추가 정보
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [Visual Studio의 Office 솔루션 아키텍처](../vsto/architecture-of-office-solutions-in-visual-studio.md)
