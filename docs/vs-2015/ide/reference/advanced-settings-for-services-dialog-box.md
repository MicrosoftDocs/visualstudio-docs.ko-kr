---
title: 서비스의 고급 설정 대화 상자 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a021475df1ade9bb6220612aad666d503c19cb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651713"
---
# <a name="advanced-settings-for-services-dialog-box"></a>서비스의 고급 설정 대화 상자
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

클라이언트 애플리케이션 서비스를 통해 Windows Forms 및 WPF(Windows Presentation Foundation) 애플리케이션에서 [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] 로그인, 역할 및 프로필 서비스에 간편하게 액세스할 수 있습니다. **프로젝트 디자이너**에서 **서비스** 페이지를 사용하여 클라이언트 애플리케이션 서비스를 구성할 수 있습니다. **서비스** 페이지에 대한 자세한 내용은 [프로젝트 디자이너, 서비스 페이지](../../ide/reference/services-page-project-designer.md)를 참조하세요.

 **프로젝트 디자이너**에서 **서비스** 페이지의 **서비스의 고급 설정** 대화 상자를 사용하여 클라이언트 애플리케이션 서비스에 대한 고급 설정을 구성합니다. 이러한 설정을 사용하여 일부 기본 애플리케이션 서비스 동작을 재정의하면 덜 일반적인 시나리오를 구현할 수 있습니다. 자세한 내용은 [클라이언트 애플리케이션 서비스](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)를 참조하세요.

 **서비스의 고급 설정** 대화 상자에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택하고 **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너**가 나타나면 **서비스** 탭을 클릭하고 **고급** 단추를 클릭합니다. 클라이언트 애플리케이션 서비스를 사용하도록 설정할 때까지 이 단추를 사용할 수 없습니다.

## <a name="task-list"></a>작업 목록
 [방법: 클라이언트 애플리케이션 서비스 구성](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

 [방법: 클라이언트 애플리케이션 서비스에서 오프라인으로 작업](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)

## <a name="uielement-list"></a>UI 요소 목록
 **오프라인으로 로그인할 수 있도록 로컬에 암호 해시 저장** 애플리케이션이 오프라인 모드에 있을 때 사용자가 로그인할 수 있도록 암호화된 형식의 사용자 암호를 로컬에서 캐시할지 여부를 지정합니다. 자세한 내용은 [방법: 클라이언트 애플리케이션 서비스에서 오프라인으로 작업](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)을 참조하세요. 이 옵션은 기본적으로 선택됩니다.

 **서버 쿠키가 만료될 때마다 다시 사용자 로그온** 애플리케이션이 역할이나 프로필 서비스에 액세스할 때 서버 인증 쿠키가 만료된 경우 이전에 인증된 사용자를 자동으로 다시 인증할지 여부를 지정합니다. 쿠키가 만료된 후 애플리케이션 서비스에 대한 액세스를 거부하고 명시적 재인증을 요구하려면 이 옵션을 선택합니다. 공용 위치에 배포된 애플리케이션에 유용한 이 옵션을 선택하면 사용한 후에도 애플리케이션을 계속 실행해 두는 사용자의 인증된 상태가 무기한으로 유지되지 않습니다. 이 옵션은 기본적으로 선택 취소되어 있습니다.

 **역할 서비스 캐시 제한 시간** 클라이언트 역할 공급자가 역할 서비스에 액세스하는 대신 캐시된 역할 값을 사용할 기간을 지정합니다. 이 시간 간격은 역할 업데이트 빈도가 높으면 작은 값으로 설정하고 빈도가 낮으면 큰 값으로 설정합니다. 기본값은 1일입니다.

 <xref:System.Web.Security.RolePrincipal.IsInRole%2A> 메서드를 호출하면 역할 공급자가 캐시된 역할 값 또는 역할 서비스에 액세스합니다. 프로그래밍 방식으로 캐시를 지우고 이 메서드가 원격 서비스에 액세스하도록 강제 지정하려면 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> 메서드를 호출합니다.

 **사용자 지정 연결 문자열 사용** 클라이언트 서비스 공급자가 로컬 캐시에 대해 사용자 지정 데이터 저장소를 사용할지 여부를 지정합니다. 기본적으로 서비스 공급자는 캐시에 대해 로컬 파일 시스템을 사용합니다. 이 옵션을 선택하면 입력란이 기본 연결 문자열로 자동으로 채워집니다. 기본 연결 문자열을 유지하여 SQL Server Compact Edition 데이터베이스를 자동으로 생성 및 사용하거나, 기존 SQL Server 데이터베이스에 대한 연결 문자열을 지정할 수 있습니다. 자세한 내용은 [방법: 클라이언트 애플리케이션 서비스 구성](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)을 참조하세요. 이 옵션은 기본적으로 선택 취소되어 있습니다.

## <a name="see-also"></a>관련 항목
 [클라이언트 애플리케이션 서비스](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [서비스 페이지, 프로젝트 디자이너](../../ide/reference/services-page-project-designer.md) [방법: 클라이언트 애플리케이션 서비스 구성](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [방법: 클라이언트 애플리케이션 서비스를 사용 하 여 오프 라인으로 작업](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
