---
title: Visual Studio의 VBA 및 Office 솔루션 비교
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24e7d3674712a17d940b94637db808c0d91d2d6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982130"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Visual Studio의 VBA 및 Office 솔루션 비교
  Microsoft VBA(Visual Basic for Applications)는 Office 애플리케이션과 긴밀하게 통합되는 비관리 코드를 사용합니다. Visual Studio를 사용하여 만든 Microsoft Office 프로젝트를 사용하면 .NET Framework 및 Visual Studio 디자인 도구를 활용할 수 있습니다.

 Visual Studio를 사용 하 여 만들 수 있는 Office 솔루션의 형식에 대 한 자세한 내용은 [office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)를 참조 하세요.

## <a name="comparison"></a>비교
 다음 표에서는 Visual Studio의 Office 솔루션과 VBA 솔루션을 기본적으로 비교합니다.

|VBA 솔루션|Visual Studio의 Office 솔루션|
|-------------------|---------------------------------------|
|특정 문서에 연결되어 유지되는 코드를 사용합니다.|문서와 별도로 저장 되는 코드 (문서 수준 사용자 지정의 경우) 나 응용 프로그램이 로드 하는 어셈블리 (VSTO 추가 기능의 경우)를 사용 합니다.|
|Office 개체 모델 및 VBA API와 작동합니다.|Office 개체 모델 및 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] API에 대한 액세스를 제공합니다.|
|매크로 기록 및 단순화된 개발자 환경을 위해 설계되었습니다.|보안, 더욱 쉬운 코드 유지 관리 및 완전한 Visual Studio IDE(통합 개발 환경)를 사용하는 기능을 위해 설계되었습니다.|
|Office 응용 프로그램과의 긴밀 한 통합을 활용 하는 솔루션에 적합 합니다.|Visual Studio 및 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]의 전체 리소스를 활용하는 솔루션에 적합합니다.|
|엔터프라이즈의 경우 제한이 있으며 보안 및 배포 영역에서 특히 제한이 있습니다.|엔터프라이즈에서 사용하기 위해 설계되었습니다.|

 일부 작업은 VBA를 사용하여 더 쉽고 빠르게 수행할 수 있습니다. 특히 다음의 경우 VBA를 계속 사용하려고 할 수 있습니다.

- 사용자 지정 워크시트 함수

- 매크로 기록

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Visual Studio를 사용 하 여 만든 VBA 솔루션과 Office 솔루션 결합
 Visual Studio를 사용하여 만든 Office 솔루션에서 VBA 코드를 호출할 수 있으며 VBA에서 Visual Studio를 사용하여 만든 Office 솔루션에서 코드를 호출할 수도 있습니다. 구체적인 방법은 Office 솔루션이 VSTO 추가 기능인지, 아니면 문서 수준 사용자 지정인지에 따라 다릅니다. 자세한 내용은 [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) 및 [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)
- [문서 수준 사용자 지정의 아키텍처](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Visual Studio에서 Office 개발 &#40;시작&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
