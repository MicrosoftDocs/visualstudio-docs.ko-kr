---
title: 서버에 있는 문서의 데이터 액세스
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ab033120c0913bbae33458c5a2d0b53972364581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255773"
---
# <a name="access-data-in-documents-on-the-server"></a>서버에 있는 문서의 데이터 액세스
  Microsoft Office Word 또는 Microsoft Office Excel의 개체 모델을 사용 하지 않고도 문서 수준 사용자 지정에서 데이터에 대해 프로그래밍할 수 있습니다. 즉, Word 또는 Excel이 설치 되지 않은 서버에서 문서에 포함 된 데이터에 액세스할 수 있습니다. 예를 들어, 서버 (예: 페이지)의 코드는 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 문서의 데이터를 사용자 지정 하 고 사용자 지정 된 문서를 최종 사용자에 게 보낼 수 있습니다. 최종 사용자가 문서를 열면 솔루션 어셈블리의 데이터 바인딩 코드가 사용자 지정 된 데이터를 문서에 바인딩합니다. 이는 문서의 데이터가 사용자 인터페이스에서 분리 되기 때문에 가능 합니다. 자세한 내용은 [문서 수준 사용자 지정의 캐시 된 데이터](../vsto/cached-data-in-document-level-customizations.md)를 참조 하세요.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>서버에서 사용할 데이터 캐시
 문서에 있는 데이터 개체를 캐시 하려면 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 디자인 타임에 특성으로 표시 하거나 `StartCaching` 런타임에 호스트 항목의 메서드를 사용 합니다. 문서에서 데이터 개체를 캐시 하는 경우는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 개체를 문서에 저장 된 XML 문자열로 serialize 합니다. 개체는 캐싱에 적합 한 특정 요구 사항을 충족 해야 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.

 서버 쪽 코드는 데이터 캐시에 있는 모든 데이터 개체를 조작할 수 있습니다. 캐시 된 데이터 인스턴스에 바인딩된 컨트롤은 사용자 인터페이스와 동기화 되므로 문서를 클라이언트에서 열 때 데이터에 적용 되는 서버측 변경 내용이 자동으로 표시 됩니다.

## <a name="access-data-in-the-cache"></a>캐시의 데이터에 액세스
 콘솔 응용 프로그램, Windows Forms 응용 프로그램, 웹 페이지 등 Office 외부의 응용 프로그램에서 캐시의 데이터에 액세스할 수 있습니다. 캐시 된 데이터에 액세스 하는 응용 프로그램에는 완전 신뢰가 필요 합니다. 부분 신뢰를 가진 웹 응용 프로그램은 Office 문서에 캐시 된 데이터를 삽입 하거나 검색 하거나 변경할 수 없습니다.

 데이터 캐시는 클래스의 속성에 의해 노출 되는 컬렉션의 계층 구조를 통해 액세스할 수 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 있습니다.

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>속성은 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> 문서 수준 사용자 지정에서 캐시 된 모든 데이터를 포함 하는을 반환 합니다.

- 각 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>에는 하나 이상의 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 개체가 포함되어 있습니다. 는 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 단일 클래스 내에 정의 된 모든 캐시 된 데이터 개체를 포함 합니다.

- 각 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>에는 하나 이상의 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 개체가 포함되어 있습니다. 는 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 캐시 된 단일 데이터 개체를 나타냅니다.

  다음 코드 예제에서는 `Sheet1` Excel 통합 문서 프로젝트의 클래스에서 캐시 된 문자열에 액세스 하는 방법을 보여 줍니다. 이 예제는 메서드에 대해 제공 된 더 큰 예제의 일부입니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> .

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>캐시에서 데이터 수정
 캐시 된 데이터 개체를 수정 하려면 일반적으로 다음 단계를 수행 합니다.

1. 캐시 된 개체의 XML 표현을 개체의 새 인스턴스로 Deserialize 합니다. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>캐시 된 데이터 개체를 나타내는의 속성을 사용 하 여 XML에 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> .

2. 이 복사본을 변경 합니다.

3. 다음 옵션 중 하나를 사용 하 여 변경 된 개체를 다시 데이터 캐시로 Serialize 합니다.

    - 변경 내용을 자동으로 직렬화 하려면 메서드를 사용 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 합니다. 이 메서드는 **DiffGram** <xref:System.Data.DataSet> <xref:System.Data.DataTable> 데이터 캐시에서, 및 형식화 된 데이터 집합 개체를 Serialize 하는 데 DiffGram 형식을 사용 합니다. **DiffGram** 형식을 사용 하면 오프 라인 문서의 데이터 캐시에 대 한 변경 내용이 서버에 올바르게 전송 됩니다.

    - 캐시 된 데이터 변경 내용에 대 한 사용자 고유의 serialization을 수행 하려는 경우 속성에 직접 쓸 수 있습니다 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> . 을 사용 **DiffGram** 하 여 <xref:System.Data.Common.DataAdapter> <xref:System.Data.DataSet> , 또는 형식화 된 데이터 집합의 데이터에 대 한 변경 내용으로 데이터베이스를 업데이트 하는 경우 DiffGram 형식을 지정 합니다 <xref:System.Data.DataTable> . 그렇지 않으면에서 <xref:System.Data.Common.DataAdapter> 기존 행을 수정 하는 대신 새 행을 추가 하 여 데이터베이스를 업데이트 합니다.

### <a name="modify-data-without-deserializing-the-current-value"></a>현재 값을 deserialize 하지 않고 데이터 수정
 일부 경우에는 현재 값을 deserialize 하지 않고 캐시 된 개체의 값을 수정 하는 것이 좋습니다. 예를 들어 문자열 또는 정수와 같이 단순 형식이 포함 된 개체의 값을 변경 하거나 서버의 문서에서 캐시 된를 초기화 하는 경우이 작업을 수행할 수 있습니다 <xref:System.Data.DataSet> . 이러한 경우에는 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 캐시 된 개체의 현재 값을 먼저 deserialize 하지 않고 메서드를 사용할 수 있습니다.

 다음 코드 예제에서는 `Sheet1` Excel 통합 문서 프로젝트의 클래스에서 캐시 된 문자열의 값을 변경 하는 방법을 보여 줍니다. 이 예제는 메서드에 대해 제공 된 더 큰 예제의 일부입니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> .

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>데이터 캐시에서 null 값 수정
 문서를 저장 하 고 닫을 때 값이 **null** 인 개체는 데이터 캐시에 저장 되지 않습니다. 캐시 된 데이터를 수정할 때 다음과 같은 제한 사항이 있습니다.

- 데이터 캐시의 개체를 **null**값으로 설정 하면 문서를 열 때 데이터 캐시의 모든 개체가 자동으로 **null** 로 설정 되 고 문서를 저장 하 고 닫을 때 전체 데이터 캐시가 지워집니다. 즉, 캐시 된 모든 개체가 데이터 캐시에서 제거 되 고 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 컬렉션이 비어 있게 됩니다.

- 데이터 캐시에 **null** 개체가 포함 된 솔루션을 빌드하고 문서를 처음 열기 전에 클래스를 사용 하 여 이러한 개체를 초기화 하려는 경우 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 데이터 캐시의 모든 개체를 초기화 해야 합니다. 일부 개체만 초기화 하면 문서를 열 때 모든 개체가 **null** 로 설정 되 고 문서를 저장 하 고 닫을 때 전체 데이터 캐시가 지워집니다.

## <a name="access-typed-datasets-in-the-cache"></a>캐시의 형식화 된 데이터 집합에 액세스
 Office 솔루션과 Office 외부 응용 프로그램 (예: Windows Forms 응용 프로그램 또는 프로젝트)에서 형식화 된 데이터 집합의 데이터에 액세스 하려는 경우 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 두 프로젝트 모두에서 참조 되는 별도의 어셈블리에 형식화 된 데이터 집합을 정의 해야 합니다. **데이터 소스 구성** 마법사나 **데이터 세트 디자이너**를 사용 하 여 각 프로젝트에 형식화 된 데이터 집합을 추가 하는 경우 .NET Framework는 두 프로젝트의 형식화 된 데이터 집합을 서로 다른 형식으로 처리 합니다. 형식화 된 데이터 집합을 만드는 방법에 대 한 자세한 내용은 [Visual Studio에서 데이터 집합 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)을 참조 하세요.

## <a name="see-also"></a>참조

- [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)
- [문서 수준 사용자 지정의 캐시 된 데이터](../vsto/cached-data-in-document-level-customizations.md)