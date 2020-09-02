---
title: Office 솔루션에서 로컬 데이터베이스 파일 사용 개요
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea260a6286c8a923d56ab7a5088b55de57004489
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982240"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Office 솔루션에서 로컬 데이터베이스 파일 사용 개요
  Office 솔루션에 SQL Server Express (*.mdf*) 파일 또는 Microsoft Office 액세스 (*.mdb*) 파일 등의 데이터베이스 파일을 포함할 수 있습니다. 이를 통해 최종 사용자는 중앙 데이터베이스를 유지 관리 하지 않아도 되는 상황에서 로컬 데이터베이스를 유지할 수 있습니다. 예를 들어 단일 컴퓨터 에서만 사용 되는 로컬 인벤토리 솔루션을 사용할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>데이터베이스 파일을 프로젝트로 가져오기
 데이터베이스 파일을 프로젝트로 가져오려면 **데이터 소스 구성 마법사** 를 사용 하 여 데이터베이스 파일을 기반으로 데이터 원본을 만듭니다. 마법사에서 데이터베이스 파일 및 형식화 된 데이터 집합을 프로젝트에 추가 합니다.

## <a name="deploy-the-database-file"></a>데이터베이스 파일 배포
 **데이터 소스 구성 마법사** 는 상대 경로를 사용 하 여 로컬 데이터베이스 파일에 대 한 연결을 만듭니다. 이렇게 하면 파일의 상대 위치를 유지 하는 경우 한 컴퓨터에서 다른 컴퓨터로 솔루션을 복사할 수 있습니다.

 서버에 솔루션을 배포 하 고 각 최종 사용자에 게 문서를 배포 하는 경우 데이터베이스 파일도 수동으로 배포 하 고 문서와 상대적인 위치에 설치 해야 합니다. 즉, 최종 사용자는 데이터베이스 파일을 이동 하는 경우를 제외 하 고는 사용자 컴퓨터의 새 위치로 문서를 이동할 수 없습니다.

## <a name="local-database-files-and-caching-the-dataset"></a>로컬 데이터베이스 파일 및 데이터 집합 캐싱
 Excel 및 Microsoft Office Word Microsoft Office 문서 수준 솔루션에서 데이터 집합 인스턴스를 특성으로 표시 하 여 문서의 데이터 집합을 캐시할 수 있습니다 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . **데이터 소스 구성 마법사**를 사용 하 여 데이터베이스 파일을 프로젝트에 추가 하면 형식화 된 데이터 집합이 프로젝트에 자동으로 추가 됩니다. <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>데이터가 사용자 컴퓨터에서 이미 로컬 이기 때문에이 데이터 집합에 적용 하는 것은 거의 필요 하지 않습니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [데이터 캐시](../vsto/caching-data.md)
