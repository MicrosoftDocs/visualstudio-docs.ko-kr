---
title: Visual Studio를 사용하여 Office용 VSTO 추가 기능 만들기
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e8cd25b8c4c70067641468dd6fa321e9e4fbe39
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809364"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Visual Studio를 사용하여 Office용 VSTO 추가 기능 만들기
  Visual Studio의 Microsoft Office 개발자 도구를 사용하여 Office를 확장하는 .NET Framework 애플리케이션을 만들 수 있습니다. 이러한 애플리케이션을 *Office 솔루션*이라고도 합니다.

 Office 개발자 도구는 다양한 비즈니스 요구 사항에 맞는 Office 솔루션을 만드는 데 사용할 수 있는 기능을 제공합니다. 이 도구에는 Visual Basic 또는 Visual C#을 사용하여 Office 솔루션을 만들 수 있는 프로젝트 템플릿과 Office 솔루션용 사용자 지정 사용자 인터페이스를 만들 수 있는 비주얼 디자이너가 포함되어 있습니다.

[!include[Add-ins note](includes/addinsnote.md)]

 Office 개발에 대 한 최신 정보는 [Microsoft Office 개발자 센터](https://developer.microsoft.com/office/docs)를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용
- [Visual Studio에서 Office 개발 &#40;시작&#41;](getting-started-office-development-in-visual-studio.md)

 Office 솔루션을 만들기 위해 개발 컴퓨터를 구성하는 방법, Office 솔루션 만들기를 시작하는 방법 및 Visual Studio에 포함된 Office 개발용 새 기능에 대한 정보 링크를 제공합니다.

- [Office 솔루션 업그레이드 및 마이그레이션](upgrading-and-migrating-office-solutions.md)

 이전 버전의 Visual Studio를 사용하여 만든 프로젝트의 업그레이드 프로세스에 대한 정보 링크를 제공합니다.

- [Visual Studio의 Office 솔루션 아키텍처](architecture-of-office-solutions-in-visual-studio.md)

 문서 수준 사용자 지정과 VSTO 추가 기능 관련 정보를 비롯한 Office 솔루션의 작동 방식에 대한 정보의 링크를 제공합니다.

- [Office 솔루션 디자인 및 만들기](designing-and-creating-office-solutions.md)

 Visual Studio에서 Office 프로젝트를 만들고 프로젝트를 구성하는 방법에 대한 정보를 제공합니다.

- [Office 솔루션 개발](developing-office-solutions.md)

 Office 사용자 인터페이스를 사용자 지정하고 데이터를 사용하고 문제를 해결하는 방법을 비롯하여 Office 솔루션에서 관리 코드를 사용하는 방법에 대한 정보를 제공합니다.

- [Excel 솔루션](excel-solutions.md)

 Excel을 자동화하고 Excel 솔루션을 만들고 Excel과 관련된 세계화 문제를 이해하는 방법에 대한 정보를 제공합니다.

- [InfoPath 솔루션](infopath-solutions.md)

 InfoPath용 양식 템플릿 및 VSTO 추가 기능을 만드는 방법에 대한 정보를 제공합니다.

- [Outlook 솔루션](outlook-solutions.md)

 Outlook을 자동화하고 Outlook VSTO 추가 기능 및 양식 영역을 만드는 방법에 대한 정보를 제공합니다.

- [PowerPoint 솔루션](powerpoint-solutions.md)

 PowerPoint를 자동화하고 PowerPoint VSTO 추가 기능을 만드는 방법에 대한 정보를 제공합니다.

- [프로젝트 솔루션](project-solutions.md)

 Project Microsoft Office 자동화 하 고 project VSTO 추가 기능을 만드는 방법에 대 한 정보를 제공 합니다.

- [Visio 솔루션](visio-solutions.md)

 Visio를 자동화하고 Visio VSTO 추가 기능을 만드는 방법에 대한 정보를 제공합니다.

- [Word 솔루션](word-solutions.md)

 Word를 자동화하고 Word 솔루션을 만드는 방법에 대한 정보를 제공합니다.

- [Office 솔루션 빌드](building-office-solutions.md)

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 Office 프로젝트와 기타 유형의 프로젝트를 빌드하는 방식 간의 차이점에 대한 정보를 제공합니다.

- [Office 프로젝트 디버그](debugging-office-projects.md)

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 Office 프로젝트와 기타 유형의 프로젝트를 디버그하는 방식 간의 차이점에 대한 정보를 제공합니다.

- [Office 솔루션 보안](securing-office-solutions.md)

 Office 솔루션의 보안 기능 작동 방식에 대한 정보를 제공합니다.

- [Office 솔루션 배포](deploying-an-office-solution.md)

 사용자에게 Office 솔루션을 제공하는 방법과 배포 방법을 선택할 때 고려해야 하는 중요한 문제에 대한 정보를 제공합니다.

- [Office 개발 샘플 및 연습](office-development-samples-and-walkthroughs.md)

 일반적인 작업을 수행하기 위한 단계별 지침을 제공하는 항목과 샘플 애플리케이션에 대한 링크를 제공합니다.

- [Visual Studio에서 Office 개발 &#40;일반 참조&#41;](general-reference-office-development-in-visual-studio.md)

 Office 주 interop 어셈블리, 매니페스트, 사용자 인터페이스 요소 및 오류 메시지에 대 한 자세한 정보를 제공 하는 링크를 제공 합니다.

- [Visual Studio에서 Office 개발을 &#40;관리 되는 참조&#41;](managed-reference-office-development-in-visual-studio.md)

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]를 대상으로 하는 Office 프로젝트에서 사용되는 API 네임스페이스 및 형식 관련 정보의 링크를 제공합니다. .NET Framework 3.5를 대상으로 하는 Office 프로젝트에서 사용 되는 네임 스페이스 및 형식에 대 한 API 참조 설명서를 보려면 Visual Studio 2008 설명서: [2007 시스템 관리 참조](managed-reference-office-development-in-visual-studio.md)에서 다음 참조 섹션을 참조 하세요.

- [Visual Studio에서 Office 개발을 &#40;관리 되지 않는 API 참조&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Office 애플리케이션의 관리되는 VSTO 추가 기능 로드/언로드와 같은 작업을 수행하는 데 사용할 수 있는 COM 인터페이스 관련 정보에 대한 링크를 제공합니다.

## <a name="related-sections"></a>관련 단원
- [Visual Studio 개발자 포털을 사용 하 여 Office 개발](https://developer.microsoft.com/office/docs) 기술 문서, 비디오, 블로그 등의 추가 리소스를 제공 합니다.

- [Visual Studio 개발자 센터](https://visualstudio.microsoft.com/) 기술 문서, 비디오, 블로그 등의 추가 Visual Studio 리소스를 제공 합니다.

- [MSDN library의 Microsoft Office 개발 섹션](/previous-versions/office/office-12/bb726434(v=office.12)) 여러 Office 버전 (Visual Studio를 사용한 Office 개발에 국한 되지 않음)에 대 한 솔루션을 개발 하는 방법에 대 한 문서 및 참조 설명서를 찾을 수 있는 MSDN 라이브러리 영역입니다.

- [Visual Studio에서 응용 프로그램 개발](/previous-versions/h8w79z10(v=vs.140)) Visual Studio를 사용 하 여 웹 응용 프로그램, XML 웹 서비스 및 기존의 클라이언트 응용 프로그램을 디자인, 개발, 디버그 및 배포 하는 방법을 설명 하는 항목의 링크를 포함 합니다.

- [Visual Studio의 .NET Framework 프로그래밍](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Visual Basic 및 Visual c #에서 .NET Framework 사용 하 여 응용 프로그램을 개발 하는 방법을 설명 합니다.