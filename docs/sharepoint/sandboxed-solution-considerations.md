---
title: 샌드박스 솔루션 고려 사항 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
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
ms.openlocfilehash: 3f6345e7627549c672aa28fac8cba5f6d9658a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841562"
---
# <a name="sandboxed-solution-considerations"></a>샌드박스 솔루션 고려 사항
  *샌드박스 솔루션* 은 Microsoft SharePoint 2010의 기능으로, 사이트 모음 사용자가 고유한 사용자 지정 코드 솔루션을 업로드할 수 있습니다. 일반적인 샌드박스가 적용 된 솔루션은 사용자가 자신의 웹 파트을 업로드 하는 것입니다.

 샌드 박싱된 SharePoint 응용 프로그램은 웹 팜 제한 된 부분에 대 한 액세스 권한이 있는 안전 하 고 모니터링 되는 프로세스에서 실행 됩니다. Microsoft SharePoint 2010은 기능, 솔루션 갤러리, 솔루션 모니터링 및 유효성 검사 프레임 워크를 조합 하 여 샌드박스 솔루션을 사용 하도록 설정 합니다.

## <a name="specify-project-trust-level"></a>프로젝트 신뢰 수준 지정
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]*샌드박스 솔루션*이라는 부울 프로젝트 속성을 통해 샌드박스가 적용 된 솔루션을 지원 합니다. 이 속성은 프로젝트에서 언제 든 지 설정 하거나 **SharePoint 사용자 지정 마법사**에서 프로젝트를 만들 때 지정할 수 있습니다.

> [!NOTE]
> 프로젝트를 만든 후에 *샌드박스 솔루션* 속성을 변경 하면 유효성 검사 오류가 발생할 수 있습니다.

 *샌드박스가 적용 된 솔루션* 속성이 **false** 로 설정 되어 있거나 **팜 솔루션으로 배포** 옵션을 선택 하면 솔루션이 팜 범위 솔루션으로 간주 됩니다. 그러나 *샌드박스가 적용 된 솔루션* 속성이 **true** 로 설정 되어 있거나 마법사에서 **샌드박스 솔루션으로 배포** 옵션을 선택 하는 경우 솔루션은 팜 솔루션과 다르게 처리 됩니다.

## <a name="sharepoint-site-hierarchy"></a>SharePoint 사이트 계층 구조
 샌드박스가 적용 되는 솔루션의 작동 방식을 이해 하기 위해 SharePoint 사이트는 범위 내에서 계층적 임을 파악 하는 데 도움이 됩니다. Top 요소를 웹 팜 이라고 하며, 다른 요소는이 요소에 종속 됩니다.

 웹 팜

 웹 응용 프로그램 A

 사이트 모음 A1

 사이트 A1a

 웹 응용 프로그램 B

 사이트 모음 B1

 사이트 B1a

 사이트 B1b

 사이트 모음 B2

 사이트 B2a

 여기에서 볼 수 있듯이 웹 팜은 하나 이상의 웹 응용 프로그램을 포함할 수 있으며,이는 하위 사이트를 포함할 수 있는 하나 이상의 사이트 컬렉션을 포함할 수 있습니다. 한 사이트 모음에 대 한 변경 내용은 해당 사이트 컬렉션에만 적용 되 고 다른 하나는 적용 되지 않습니다. 그러나 웹 팜 수준에서 변경한 내용은 팜의 모든 사이트 모음에 영향을 줍니다.

 WSS (Windows SharePoint Services) 3.0는 팜 수준에만 솔루션을 배포할 수 있도록 하지만 팜 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 수준 (팜 솔루션) 또는 사이트 모음 수준 (샌드박스가 적용 된 솔루션)에 배포할 수 있습니다.

## <a name="why-sandboxed-solutions"></a>샌드박스가 적용 된 솔루션은 무엇 인가요?
 WSS 3.0에서 솔루션은 팜 수준에만 배포할 수 있습니다. 즉, 전체 웹 팜 및 그 아래에서 실행 되는 다른 모든 사이트 모음 및 응용 프로그램에 영향을 주는 잠재적으로 유해한 또는 불안정 솔루션을 배포할 수 있습니다. 그러나 샌드박스가 적용 된 솔루션을 사용 하면 특정 사이트 컬렉션인 팜의 하위 영역에 솔루션을 배포할 수 있습니다. 추가 보호를 제공 하기 위해 솔루션의 어셈블리가 주 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 프로세스 (*w3wp.exe*)에 로드 되지 않습니다. 대신 별도의 프로세스 (*SPUCWorkerProcess.exe*)로 로드 됩니다. 이 프로세스를 모니터링 하 고 할당량 및 제한을 구현 하 여 CPU 사이클을 소비 하는 루프 실행과 같은 해로운 활동을 수행 하는 샌드 박싱된 솔루션 으로부터 팜을 보호 합니다.

## <a name="site-collection-solution-gallery"></a>사이트 모음 솔루션 갤러리
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010에는 "사이트 컬렉션 솔루션 갤러리"라는 기능이 있습니다. SharePoint 2010 중앙 관리 페이지에서 또는 **사이트 작업** 메뉴를 열고 **사이트 설정**을 선택한 다음 sharepoint 사이트의 **갤러리** 아래에서 **솔루션** 링크를 선택 하 여이 기능에 액세스할 수 있습니다. 솔루션 갤러리는 사이트 모음 관리자가 사이트 모음에서 솔루션을 관리할 수 있는 솔루션의 리포지토리입니다.

 솔루션 갤러리는 SharePoint 사이트의 루트 웹에 저장 된 문서 라이브러리입니다. 솔루션 갤러리는 사이트 템플릿을 대체 하 고 솔루션 패키지를 지원 합니다. SharePoint 솔루션 패키지 (*.wsp*) 파일을 업로드 하면 샌드박스가 적용 된 솔루션으로 처리 됩니다.

## <a name="sandboxed-solution-limitations"></a>샌드박스 솔루션 제한 사항
 샌드박스가 적용 된 솔루션을 배포 하는 경우 해당 솔루션에서 사용할 수 있는 SharePoint 기능의 배열은 보유 한 보안 취약성을 줄이는 데 도움이 됩니다. 이러한 제한 사항 중 일부는 다음과 같습니다.

- 샌드박스 솔루션에는 사용할 수 있는 배포 가능 솔루션 요소의 제한 된 하위 집합이 있습니다. 사이트 정의 및 워크플로와 같은 잠재적으로 취약 한 SharePoint 프로젝트 템플릿을 사용할 수 없습니다.

- SharePoint는w3wp.exe(주* * [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 응용 프로그램 풀) 프로세스와 분리 된 프로세스 (SPUCWorkerProcess.exe)에서* *샌드박스 솔루션 코드를 실행 합니다.

- 매핑된 폴더를 프로젝트에 추가할 수 없습니다.

- 어셈블리의 형식은 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 샌드박스가 적용 된 솔루션에서 사용할 수 없습니다. 또한 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 어셈블리 Microsoft. SharePoint의 형식만 샌드박스 솔루션에서 사용할 수 있습니다.

  Sharepoint 솔루션을 샌드박스 솔루션으로 지정 하면 SharePoint 서버에 영향을 주지 않는다는 점에 유의 해야 합니다. SharePoint 프로젝트를 SharePoint에 배포 하는 방법 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 및이를 바인딩할 어셈블리를 결정 합니다. 이는 생성 된 *.wsp* 파일에는 영향을 주지 않으며 *.wsp* 파일에는 *샌드박스가 적용 된 솔루션* 속성에 직접 연관 된 데이터가 없습니다.

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>샌드박스가 적용 된 솔루션의 기능 및 요소
 샌드박스가 적용 된 솔루션은 다음과 같은 기능 및 요소를 지원 합니다.

- 콘텐츠 형식/필드

- 사용자 지정 작업

- 선언적 워크플로

- 이벤트 수신자

- 기능 설명선

- 정의 나열

- 목록 인스턴스

- 모듈/파일

- 탐색

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- 에서 파생 되는 모든 웹 파트에 대 한 지원 `System.Web.UI.WebControls.WebParts.WebPart`

- 웹 파트

- WebTemplate 기능 요소 ( *Webtemp.xml*대신)

- Visual 웹 파트

  샌드박스가 적용 된 솔루션은 다음과 같은 기능 및 요소를 지원 하지 않습니다.

- 응용 프로그램 페이지

- 사용자 지정 작업 그룹

- 팜 범위 기능

- `HideCustomAction` 요소

- 웹 응용 프로그램 범위 기능

- 코드를 사용 하는 워크플로

## <a name="see-also"></a>참고 항목
- [샌드박스가 적용 된 솔루션과 팜 솔루션의 차이점](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
