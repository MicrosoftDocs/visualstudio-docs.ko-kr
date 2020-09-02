---
title: 데이터 캐시
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e0f6d7fcf9920ddb8861712b7c5f8bf04506fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62939417"
---
# <a name="cache-data"></a>데이터 캐시
  문서 수준 사용자 지정에서 데이터 개체를 캐시 하 여 데이터를 오프 라인으로 액세스 하거나 Word Microsoft Office 또는 Microsoft Office Excel을 열지 않고도 데이터에 액세스할 수 있습니다. 개체를 캐시 하려면 개체에 특정 요구 사항을 충족 하는 데이터 형식이 있어야 합니다. .NET Framework의 많은 일반적인 데이터 형식은, 및를 포함 하 여 이러한 요구 사항을 충족 <xref:System.String> <xref:System.Data.DataSet> <xref:System.Data.DataTable> 합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 데이터 캐시에 개체를 추가 하는 방법에는 다음 두 가지가 있습니다.

- 솔루션을 빌드할 때 데이터 캐시에 개체를 추가 하려면 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 개체 선언에 특성을 적용 합니다. 자세한 내용은 [방법: 오프 라인 이나 서버에서 사용할 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)를 참조 하세요.

- 런타임에 프로그래밍 방식으로 데이터 캐시에 개체를 추가 하려면 `StartCaching` 또는 클래스와 같은 호스트 항목의 메서드를 사용 합니다 `ThisDocument` `ThisWorkbook` . 자세한 내용은 [방법: Office 문서에서 프로그래밍 방식으로 데이터 원본 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)를 참조 하세요.

  데이터 캐시에 개체를 추가한 후에는 Word 또는 Excel을 시작 하지 않고 캐시 된 데이터에 액세스 하 고 수정할 수 있습니다. 자세한 내용은 [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)를 참조 하세요.

## <a name="requirements-for-data-objects-to-be-cached"></a>캐시할 데이터 개체에 대 한 요구 사항
 솔루션에 데이터 개체를 캐시 하려면 개체가 다음과 같은 요구 사항을 충족 해야 합니다.

- 또는 클래스와 같은 호스트 항목의 읽기/쓰기 공용 필드 또는 속성 이어야 `ThisDocument` `ThisWorkbook` 합니다.

- 인덱서 또는 다른 매개 변수가 있는 속성이 아닙니다.

  또한 클래스를 사용 하 여 데이터 개체를 serialize 할 수 있어야 합니다 <xref:System.Xml.Serialization.XmlSerializer> . 즉, 개체의 형식에 다음과 같은 특징이 있어야 합니다.

- 공용 형식 이어야 합니다.

- 매개 변수가 없는 public 생성자가 있습니다.

- 추가 보안 권한이 필요한 코드를 실행 하지 않습니다.

- 읽기/쓰기 public 속성만 노출 합니다 (다른 속성은 무시 됨).

- 다차원 배열을 노출 하지 않습니다. 중첩 된 배열은 허용 됩니다.

- 속성 및 필드에서 인터페이스를 반환 하지 않습니다.

- <xref:System.Collections.IDictionary>컬렉션이 면을 구현 하지 않습니다.

  데이터 개체를 캐시 하면는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 개체를 문서의 *사용자 지정 xml 부분* 에 저장 된 xml 문자열로 serialize 합니다. 자세한 내용은 [사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)를 참조 하세요.

## <a name="cached-data-size-limits"></a>캐시 된 데이터 크기 제한
 문서의 데이터 캐시에 추가할 수 있는 데이터의 전체 양과 데이터 캐시의 개별 개체 크기에는 몇 가지 제한이 있습니다. 이러한 제한을 초과 하면 데이터가 데이터 캐시에 저장 될 때 응용 프로그램이 예기치 않게 닫힐 수 있습니다.

 이러한 제한을 방지 하려면 다음 지침을 따르세요.

- 10mb 보다 큰 개체는 데이터 캐시에 추가 하지 마십시오.

- 단일 문서의 데이터 캐시에 100를 초과 하는 총 데이터를 추가 하지 마세요.

  근사 값입니다. 정확한 제한은 사용 가능한 RAM 및 실행 중인 프로세스 수를 비롯 한 여러 요인에 따라 달라 집니다.

## <a name="control-the-behavior-of-cached-objects"></a>캐시 된 개체의 동작 제어
 캐시 된 개체의 동작을 보다 효율적으로 제어 하기 위해 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 캐시 된 개체의 형식에 대해 인터페이스를 구현할 수 있습니다. 예를 들어, 개체가 변경 될 때 사용자에 게 알림이 표시 되는 방식을 제어 하려는 경우이 인터페이스를 구현할 수 있습니다. 을 구현 하는 방법을 보여 주는 코드 예제는 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> `ControlCollection` [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 Excel Dynamic Controls 샘플 및 Word dynamic controls 샘플의 클래스를 참조 하세요.

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>암호로 보호 된 문서에 캐시 된 데이터에 대 한 변경 내용 유지
 암호로 보호 되는 문서에 데이터 개체를 캐시 하는 경우 캐시 된 데이터에 대 한 변경 내용은 저장 되지 않습니다. 두 개의 메서드를 재정의 하 여 캐시 된 데이터에 대 한 변경 내용을 저장할 수 있습니다. 문서를 저장할 때 보호를 일시적으로 제거 하려면 이러한 메서드를 재정의 하 고 저장 작업이 완료 되 면 보호를 다시 적용 합니다.

 자세한 내용은 [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)를 참조 하세요.

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>데이터 캐시에 null 값을 추가 하는 경우 데이터 손실 방지
 데이터 캐시에 개체를 추가 하는 경우 문서를 저장 하 고 닫기 전에 캐시 된 모든 개체를**null** 이 아닌 값으로 초기화 해야 합니다. 문서를 저장 하 고 닫을 때 캐시 된 개체에 **null** 값이 있는 경우는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 캐시 된 모든 개체를 데이터 캐시에서 자동으로 제거 합니다.

 디자인 타임에 특성을 사용 하 여 **null** 값이 포함 된 개체를 데이터 캐시에 추가 하는 경우 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 문서를 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 열기 전에 클래스를 사용 하 여 캐시 된 데이터 개체를 초기화할 수 있습니다. 이는 최종 사용자가 문서를 열기 전에 Word 또는 Excel이 설치 되지 않은 서버에서 캐시 된 데이터를 초기화 하려는 경우에 유용 합니다. 자세한 내용은 [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: 오프 라인 이나 서버에서 사용할 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [방법: Office 문서에서 프로그래밍 방식으로 데이터 소스 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [연습: 캐시 된 데이터 집합을 사용 하 여 마스터 세부 관계 만들기](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
