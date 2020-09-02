---
title: 샌드박스 솔루션과 팜 솔루션의 차이점 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967548"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>샌드박스가 적용 된 솔루션과 팜 솔루션의 차이점
  SharePoint 솔루션을 컴파일하면 sharepoint 서버에 배포 되 고 디버거가 디버그에 연결 됩니다. 솔루션을 디버깅 하는 데 사용 되는 프로세스는 샌드박스가 적용 된 솔루션 속성: 샌드박스가 적용 된 솔루션 또는 팜 솔루션의 설정에 따라 달라 집니다.

 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

## <a name="farm-solutions"></a>팜 솔루션
 IIS 작업자 프로세스 (W3WP.exe)에서 호스트 되는 팜 솔루션은 전체 팜에 영향을 줄 수 있는 코드를 실행 합니다. 샌드박스가 적용 된 솔루션 속성이 "팜 솔루션"으로 설정 된 SharePoint 프로젝트를 디버깅할 때 시스템의 IIS 응용 프로그램 풀은 IIS 작업자 프로세스에서 잠긴 파일을 해제 하기 위해 기능을 해제 하거나 배포 하기 전에 재생 됩니다. SharePoint 프로젝트의 사이트 URL을 처리 하는 IIS 응용 프로그램 풀만 재활용 됩니다.

## <a name="sandboxed-solutions"></a>샌드박스 솔루션
 SharePoint 사용자 코드 솔루션 작업자 프로세스 (SPUCWorkerProcess.exe)에서 호스팅되는 샌드박스가 적용 된 솔루션은 솔루션의 사이트 컬렉션에만 영향을 줄 수 있는 코드를 실행 합니다. 샌드박스가 적용 된 솔루션은 IIS 작업자 프로세스에서 실행 되지 않으므로 IIS 응용 프로그램 풀과 IIS 서버는 모두 다시 시작 해야 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint의 SPUserCodeV4 서비스가 자동으로 트리거 및 컨트롤을 Spucworkerprocess.exe 프로세스에 디버거를 연결 합니다. Spucworkerprocess.exe 프로세스를 재활용 하 여 최신 버전의 솔루션을 로드할 필요는 없습니다.

## <a name="either-type-of-solution"></a>두 가지 솔루션 유형
 둘 중 하나를 사용 하 여 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 브라우저에 디버거를 연결 하면 클라이언트 쪽 스크립트 디버깅을 사용 하도록 설정할 수 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는이를 위해 스크립트 디버깅 엔진을 사용 합니다. 스크립트 디버깅을 사용 하도록 설정 하려면 메시지가 표시 되 면 기본 브라우저 설정을 변경 해야 합니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 현재 사이트를 실행 하는 w3wp.exe 또는 Spucworkerprocess.exe 프로세스에만 디버거를 연결 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 또한 관리 되는 COM Plus 및 워크플로 디버깅 엔진을 연결 합니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 디버깅](../sharepoint/debugging-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)
