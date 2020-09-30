---
title: Office 솔루션의 응용 프로그램 및 배포 매니페스트
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc4095ce8cd945ff35903c9d8ffc95400cc3b7ab
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584440"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Office 솔루션의 응용 프로그램 및 배포 매니페스트
  애플리케이션 매니페스트는 Office 솔루션에서 어셈블리를 찾고 업데이트하는 데 사용되는 정보를 제공하는 XML 파일입니다. 애플리케이션 매니페스트는 배포 매니페스트와 함께 사용할 수 있습니다. 배포 매니페스트는 서버에 저장된 XML 파일로, 최신 버전의 애플리케이션 매니페스트 및 어셈블리를 찾는 데 필요한 정보를 제공합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Office 솔루션의 매니페스트 구조
 Visual Studio에서 Office 개발 도구를 사용하여 만든 Microsoft Office 솔루션의 경우 모든 매니페스트는 표준 ClickOnce 스키마를 기반으로 합니다. Office 솔루션을 배포할 때 문서 수준 및 VSTO 추가 기능 프로젝트의 애플리케이션 매니페스트는 ClickOnce 캐시에 있습니다. 배포 매니페스트는 클라이언트 컴퓨터에 복사되지 않습니다.

 Office 프로젝트용 응용 프로그램 및 배포 매니페스트의 내용에 대 한 자세한 내용은 office [솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md) 및 [office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)를 참조 하세요.

## <a name="create-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트 만들기
 애플리케이션 매니페스트는 빌드 프로세스의 일부로 자동으로 생성됩니다. 문서 수준 프로젝트를 빌드할 때마다 배포 매니페스트의 위치가 사용자 지정 문서 속성으로 문서에 포함됩니다. VSTO 추가 기능의 경우 배포 매니페스트의 위치는 레지스트리에 저장됩니다.

 **게시 마법사**에 대 한 자세한 내용은 ClickOnce를 [사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)를 참조 하세요.

 매니페스트가 Office 솔루션과 작동 하는 방식에 대 한 자세한 내용은 [office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [문서 수준 사용자 지정의 아키텍처](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)