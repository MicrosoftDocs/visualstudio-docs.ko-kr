---
title: Office 솔루션 개발 개요 (VSTO)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abb58d30e33ab5cfe713175b40cd32f593921ae9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80543945"
---
# <a name="office-solutions-development-overview-vsto"></a>Office 솔루션 개발 개요 (VSTO)
  Microsoft Office를 솔루션의 프런트 엔드로 사용하여 Word의 워드 프로세싱 기능, Excel의 데이터 분석 기능 및 Outlook의 전자 메일 관리 기능과 같은 익숙한 Microsoft Office 사용자 인터페이스 및 도구를 활용할 수 있습니다. Visual Studio에서 솔루션을 개발하여 Office 애플리케이션을 사용자 지정하고 비즈니스 프로세스에 필요한 특정 기능을 추가할 수 있습니다. 예를 들어 편집 가능하거나 편집 가능하지 않게 만들 수 있는 기존 부분에서 계약을 구성하는 계약 생성기로 Word를 전환할 수 있습니다. Excel을 사용하여 다양한 프로젝트에 대해 사용자 지정된 자동화된 예산 워크시트를 만들 수 있습니다. 또한 사용자가 Office 솔루션을 오프라인으로 전환하여 복잡한 솔루션을 웹 기반 아키텍처를 사용하는 경우보다 실용적으로 만들 수도 있습니다.

 이 항목에서는 Visual Studio의 Office 개발자 도구에서 사용할 수 있는 VSTO(Visual Studio Tools for Office) 템플릿을 사용하여 만들 수 있는 Office 솔루션의 형식에 대해 개괄적으로 설명합니다. Office를 사용 하 여 개발 하는 방법에 대 한 일반적인 내용은 [office 개발자 센터](https://developer.microsoft.com/office)를 참조 하세요.

## <a name="choose-an-office-project-type"></a>Office 프로젝트 형식 선택
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 VSTO 기반 Office 개발을 위해 다음과 같은 형식의 프로젝트 템플릿을 제공합니다.

- **문서 수준 사용자 지정** 은 특정 문서와 연결됩니다.

- **VSTO Add-ins** 은 애플리케이션 자체와 연결됩니다.

  이러한 프로젝트 형식 중 솔루션에 가장 적합한 것을 결정하려면 특정 문서가 열려 있을 때만 코드가 실행되도록 할지 여부나 애플리케이션이 실행 중일 때 코드를 항상 사용할 수 있도록 할지 여부에 대해 고려합니다. 프로젝트 템플릿에 대 한 자세한 내용은 [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)를 참조 하세요.

  만들 수 있는 프로젝트의 형식은 개발 컴퓨터에 설치한 Office 애플리케이션에 따라 다릅니다. 자세한 내용은 [Office 응용 프로그램 및 프로젝트 형식에 따라 사용 가능한 기능](../vsto/features-available-by-office-application-and-project-type.md)을 참조 하세요.

### <a name="document-level-customizations"></a>문서 수준 사용자 지정
 문서 수준 사용자 지정은 Microsoft Office Word 또는 Microsoft Office Excel의 단일 문서, 통합 문서 또는 서식 파일과 연결된 어셈블리로 구성됩니다. 어셈블리는 연결된 문서가 열릴 때 로드됩니다. 사용자 지정에서 만든 기능은 연결된 문서가 열려 있을 때만 사용할 수 있습니다. 사용자 지정에서는 문서가 열려 있을 때 새 메뉴 항목이나 리본 탭을 표시하는 것과 같은 애플리케이션 범위의 변경을 할 수 없습니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에는 문서 수준 사용자 지정을 만드는 데 도움이 되는 도구가 포함되어 있습니다. 사용자 지정하는 문서는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 디자인 화면으로 호스트되므로 컨트롤을 디자인 화면으로 끌어 놓아서 문서를 디자인할 수 있습니다. Windows Forms 컨트롤, 끌어서 놓기 데이터 바인딩, 통합된 디버거 등의 다른 많은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 기능을 문서 수준 프로젝트에서 사용할 수 있습니다.

 사용자 지정에 대한 자세한 내용은 다음 항목을 참조하세요.

- [Excel 용 문서 수준 사용자 지정 프로그래밍 시작](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Word 용 문서 수준 사용자 지정 프로그래밍 시작](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [문서 수준 사용자 지정의 아키텍처](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>VSTO 추가 기능
 VSTO 추가 기능은 Microsoft Office 애플리케이션과 연결된 어셈블리로 구성됩니다. 일반적으로 VSTO 추가 기능은 연결된 애플리케이션이 시작될 때 실행되지만 사용자는 애플리케이션이 이미 실행 중인 경우에도 VSTO 추가 기능을 로드할 수 있습니다. VSTO 추가 기능에서 만든 기능은 열려 있는 문서에 관계없이 애플리케이션 자체에서 사용할 수 있습니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에는 VSTO 추가 기능을 만드는 데 도움이 되는 도구가 포함 되어 있습니다. 추가 기능 프로젝트에는 VSTO 추가 기능을 나타내는 자동으로 생성 된 클래스가 포함 됩니다. 이 클래스는 호스트 애플리케이션의 개체 모델에 액세스하고 VSTO 추가 기능이 로드되고 종료될 때 코드를 실행하는 데 사용할 수 있는 속성과 이벤트를 제공합니다. Windows Forms, 통합된 디버거 등의 다른 많은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 기능을 VSTO 추가 기능 프로젝트에서 사용할 수 있습니다.

 VSTO 추가 기능에 대한 자세한 내용은 다음 항목을 참조하세요.

- [VSTO 추가 기능 프로그래밍 시작](../vsto/getting-started-programming-vsto-add-ins.md)

- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>주 interop 어셈블리를 사용 하 여 Office 응용 프로그램 자동화
 애플리케이션의 개체 모델에 액세스하는 코드를 작성하여 Office 애플리케이션의 기능을 프로그래밍 방식으로 솔루션에 통합할 수 있습니다. 개체 모델은 다양한 속성 및 메서드를 통해 기능을 노출하는 클래스의 배열입니다. 각 Office 애플리케이션의 개체 모델은 서로 다릅니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 Office 개발 도구를 사용하여 만든 솔루션에서 Office 애플리케이션의 개체 모델을 사용하려면 애플리케이션에 PIA(주 interop 어셈블리)를 사용해야 합니다. PIA를 사용하면 솔루션의 관리 코드가 Office 애플리케이션의 COM 기반 개체 모델과 상호 작용할 수 있습니다.

 대부분의 개발 작업을 수행하려면 개발 컴퓨터의 전역 어셈블리 캐시에서 Office PIA를 설치하고 등록해야 합니다. 자세한 내용은 [Office 솔루션을 개발할 수 있도록 컴퓨터 구성](../vsto/configuring-a-computer-to-develop-office-solutions.md)을 참조 하세요. 최종 사용자 컴퓨터에서는 VSTO Office 솔루션을 실행하는 데 Office PIA가 필요하지 않습니다. 자세한 내용은 [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)를 참조 하세요.

 VSTO Office 솔루션에서 PIA를 사용하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.

- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)

- [Office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>최종 사용자 컴퓨터에서 Microsoft VSTO Office 솔루션 실행
 VSTO Office 솔루션을 만드는 경우 배포 요구 사항이 개발 선택 사항에 미칠 수 있는 영향을 고려합니다.

### <a name="deployment-options"></a>배포 옵션
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 Office 개발 도구를 사용하여 만든 솔루션을 배포하는 데 ClickOnce 또는 Windows Installer를 사용할 수 있습니다. ClickOnce 배포를 사용하면 최소한의 사용자 조작으로 설치하고 실행할 수 있는 자동 업데이트 솔루션을 만들 수 있습니다. Windows Installer (*.msi*) 파일은 최종 사용자 컴퓨터에 쉽게 배포 하거나 SMS (Systems Management Server)를 사용 하 여 배포할 수 있습니다. VSTO Office 솔루션을 배포 하는 방법에 대 한 자세한 내용은 [office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

### <a name="install-prerequisites"></a>필수 구성 요소 설치
 최종 사용자가 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 Office 개발 도구를 사용하여 만든 솔루션을 실행하려면 컴퓨터에 특정한 필수 구성 요소가 설치되어 있어야 합니다. ClickOnce를 사용하거나 Windows Installer 파일을 만들어 솔루션을 배포하는 경우 이러한 필수 구성 요소를 솔루션과 함께 설치할 수 있습니다. 자세한 내용은 [office 솔루션 배포를 위한 필수 조건](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) 및 [방법: office 솔루션을 실행 하기 위해 최종 사용자 컴퓨터에 필수 구성 요소 설치](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)를 참조 하세요.

### <a name="security"></a>보안
 VSTO Office 솔루션의 보안은 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 에서 솔루션을 설치하고 로드할 때 수행하는 일련의 검사를 통해 적용됩니다. 이러한 검사에는 배포 매니페스트의 위치를 신뢰할 수 있는지 여부나 배포 매니페스트에 서명하는 데 사용되는 인증서를 신뢰할 수 있는지 여부의 확인이 포함됩니다. 자세한 내용은 [Office 솔루션 보안](../vsto/securing-office-solutions.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Visual Studio에서 Office 개발 &#40;시작&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [문서 수준 사용자 지정의 아키텍처](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Excel 용 문서 수준 사용자 지정 프로그래밍 시작](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Word 용 문서 수준 사용자 지정 프로그래밍 시작](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [VSTO 추가 기능 프로그래밍 시작](../vsto/getting-started-programming-vsto-add-ins.md)
