---
title: SharePoint 솔루션에 대 한 보안 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc1449a40528670274ea5b275cca3f0a8d2f277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983783"
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint 솔루션에 대 한 보안
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에는 SharePoint 응용 프로그램의 보안을 강화 하는 데 도움이 되는 다음 기능이 포함 되어 있습니다.

## <a name="safe-control-entries"></a>안전 컨트롤 항목
 에서 만든 모든 SharePoint 프로젝트 항목 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에는 safe controls 컬렉션을 나타내는 **Safe 컨트롤 항목** 속성이 있습니다. **Safe** 하위 속성을 사용 하면 안전 하다 고 생각 되는 컨트롤을 지정할 수 있습니다. 자세한 내용은 [프로젝트 항목의 패키지 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 및 [Safe 웹 파트 지정](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts)을 참조 하세요.

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers 특성
 기본적으로 런타임 CAS (코드 액세스 보안) 시스템에서 완전히 신뢰할 수 있는 응용 프로그램만 공유 된 관리 코드 어셈블리에 액세스할 수 있습니다. 완전히 신뢰할 수 있는 어셈블리를 AllowPartiallyTrustedCallers 특성으로 표시 하면 부분적으로 신뢰할 수 있는 어셈블리에 액세스할 수 있습니다.

 AllowPartiallyTrustedCallers 특성은 시스템 전역 어셈블리 캐시 ()에 배포 되지 않은 모든 SharePoint 솔루션에 추가 됩니다 [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] . 여기에는 SharePoint 응용 프로그램 Bin 디렉터리에 배포 된 샌드박스가 적용 된 솔루션 또는 솔루션이 포함 됩니다. 자세한 내용은 [버전 1 Microsoft .NET Framework의 보안 변경 내용](/previous-versions/msp-n-p/ff921345(v=pandp.10)) 및 [SharePoint Foundation의 웹 파트 배포](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))를 참조 하세요.

## <a name="safe-against-script-property"></a>Safe 스크립트 속성
 *스크립트 삽입* 은 잠재적으로 악의적인 코드를 컨트롤이 나 웹 페이지에 삽입 하는 것입니다. 스크립트 삽입 으로부터 SharePoint 2010 사이트를 보호 하기 위해 참가자는 기본적으로 웹 파트 또는 해당 속성을 보거나 편집할 수 없습니다. 이 동작은 SafeAgainstScript 라는 SafeControl 특성에 의해 제어 됩니다. 에서 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] **스크립트에 대해**프로젝트 항목의 **안전 컨트롤 항목** 하위 속성에 대해이 특성을 안전 하 게 설정 합니다. 자세한 내용은 [프로젝트 항목의 패키지 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 및 [방법: 컨트롤을 안전 컨트롤로 표시](../sharepoint/how-to-mark-controls-as-safe-controls.md)를 참조 하세요.

## <a name="vista-and-windows-7-user-account-control"></a>Vista 및 Windows 7 사용자 계정 컨트롤
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 및 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 에는 UAC (사용자 계정 컨트롤) 라는 보안 기능이 포함 되어 있습니다. 및 시스템에서 SharePoint 솔루션을 개발 하려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] UAC를 시스템 관리자로 실행 해야 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다. **시작** 메뉴에서에 대 한 바로 가기 메뉴를 연 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음 **관리자 권한으로 실행**을 선택 합니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]항상 관리자 권한으로 실행 되도록 바로 가기를 구성 하려면 해당 바로 가기 메뉴를 열고 **속성**을 선택한 다음 **속성** 대화 상자에서 **고급** 단추를 선택 하 고 **관리자 권한으로 실행** 확인란을 선택 합니다.

 자세한 내용은 [Windows Vista에서 사용자 계정 컨트롤 이해 및 구성](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10))을 참조 하세요. 및 [Windows 7 사용자 계정 컨트롤](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10))

## <a name="sharepoint-permissions-considerations"></a>SharePoint 사용 권한 고려 사항
 SharePoint 솔루션을 개발 하려면 SharePoint 솔루션을 실행 하 고 디버그할 수 있는 충분 한 권한이 있어야 합니다. SharePoint 솔루션을 테스트 하려면 먼저 다음 단계를 수행 하 여 필요한 권한이 있는지 확인 합니다.

1. 사용자 계정을 시스템의 관리자로 추가 합니다.

2. 사용자 계정을 SharePoint 서버에 대 한 팜 관리자로 추가 합니다.

    1. SharePoint 2010 중앙 관리에서 **팜 관리자 그룹 관리** 링크를 선택 합니다.

    2. **팜 관리자** 페이지에서 **새로 만들기** 메뉴 옵션을 선택 합니다.

3. 사용자 계정을 WSS_ADMIN_WPG 그룹에 추가 합니다.

## <a name="additional-security-resources"></a>추가 보안 리소스
 보안 문제에 대 한 자세한 내용은 다음을 참조 하세요.

### <a name="visual-studio-security"></a>Visual Studio 보안

- [보안 및 사용자 권한](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [네이티브 및 .NET Framework 코드의 보안](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [.NET Framework의 보안](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>SharePoint 보안

- [SharePoint Foundation 관리 및 보안](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [SharePoint 보안 리소스 센터](/sharepoint/dev/)

- [SharePoint Foundation의 웹 파트 보안](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [웹 응용 프로그램 보안 향상: 위협 및 대책](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>일반 보안

- [MSDN 보안 개발 수명 주기](https://www.microsoft.com/msrc?rtc=1)

- [보안된 ASP.NET 응용 프로그램 빌드: 인증, 권한 부여 및 보안 통신](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>추가 정보

- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)