---
title: .NET 4.5로 마이그레이션된 Office 프로젝트에 필요한 변경 내용
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40db3cd629f2c3a2ced37a781dea3244a3f19957
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584466"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>.NET 4.5로 마이그레이션된 Office 프로젝트에 필요한 변경 내용

  Office 프로젝트의 대상 프레임 워크가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이전 버전의 .NET Framework에서 이상으로 변경 된 경우 다음 작업을 수행 하 여 개발 컴퓨터와 최종 사용자 컴퓨터에서 솔루션을 실행할 수 있는지 확인 해야 합니다.

- Visual Studio 2008에서 업그레이드한 경우 프로젝트에서 <xref:System.Security.SecurityTransparentAttribute>를 제거합니다.

- 개발 컴퓨터에서 프로젝트를 실행 하거나 디버그할 수 있도록 Visual Studio에서 **정리** 명령을 수행 합니다.

- 프로젝트에 대한 .NET Framework 필수 조건을 업데이트합니다.

- 또한 대상 프레임워크를 변경하기 전에 ClickOnce를 사용하여 이전에 배포한 경우 최종 사용자가 솔루션을 다시 설치해야 합니다.

  이러한 각 작업에 대한 자세한 내용은 아래 해당 섹션을 참조하세요.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Visual Studio 2008에서 업그레이드 하는 프로젝트에서 SecurityTransparent 특성을 제거 합니다.
 Visual Studio 2008에서 Office 프로젝트를 업그레이드하고 프로젝트의 대상 프레임워크가 이후에 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경되는 경우 프로젝트에서 <xref:System.Security.SecurityTransparentAttribute>를 제거해야 합니다. Visual Studio에서 자동으로 이 특성을 제거하지 않습니다. 이 특성을 제거하지 않으면 프로젝트를 컴파일할 때 오류 메시지가 수신됩니다.

 Visual Studio에서 업그레이드 된 프로젝트의 대상 프레임 워크를 또는로 변경할 수 있는 조건에 대 한 자세한 내용은 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [Office 솔루션 업그레이드 및 마이그레이션](../vsto/upgrading-and-migrating-office-solutions.md)을 참조 하세요.

#### <a name="to-remove-the-securitytransparentattribute"></a>SecurityTransparentAttribute를 제거하려면

1. Visual Studio에서 프로젝트를 열고 **솔루션 탐색기**를 엽니다.

2. **속성** 노드(C#의 경우) 또는 **My Project** 노드(Visual Basic의 경우) 아래에서 AssemblyInfo 코드 파일을 두 번 클릭하여 코드 편집기에서 엽니다.

    > [!NOTE]
    > Visual Basic 프로젝트에서 AssemblyInfo 코드 파일을 보려면 **솔루션 탐색기** 에서 **모든 파일 표시** 단추를 클릭해야 합니다.

3. <xref:System.Security.SecurityTransparentAttribute>를 찾아 파일에서 제거하거나 주석으로 처리합니다.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>정리 명령을 수행 하 여 개발 컴퓨터에서 프로젝트를 디버그 하거나 실행 합니다.
 프로젝트의 대상 프레임 워크가 이상 버전으로 변경 되기 전에 Office 프로젝트를 빌드한 경우에는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] **정리** 명령을 수행 하 고 대상 프레임 워크가 변경 된 후에 프로젝트를 다시 빌드해야 합니다. **Clean** 명령을 수행 하지 않으면 <xref:System.Runtime.InteropServices.COMException> 대상이 변경 된 프로젝트를 디버그 하거나 실행 하려고 할 때가 표시 됩니다.

 **Clean** 명령에 대 한 자세한 내용은 [Office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조 하세요.

## <a name="update-the-prerequisites-for-deployment"></a>배포에 대 한 필수 구성 요소 업데이트
 Office 프로젝트의 대상을 이상으로 변경 하는 경우 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] **필수 구성 요소** 대화 상자 에서도 해당 .NET Framework 필수 구성 요소를 업데이트 해야 합니다. 그렇지 않으면 ClickOnce 배포 또는 InstallShield Limited Edition 프로젝트가 이전 버전의 .NET Framework를 검사하고 설치합니다.

 최종 사용자 컴퓨터에 배포 하기 위한 필수 구성 요소를 업데이트 하는 방법에 대 한 자세한 내용은 [방법: 최종 사용자 컴퓨터에 Office 솔루션 실행을 위한 필수 구성 요소 설치](/previous-versions/bb608608(v=vs.110))를 참조 하세요.

## <a name="reinstall-solutions-on-end-user-computers"></a>최종 사용자 컴퓨터에 솔루션 다시 설치
 ClickOnce를 사용하여 .NET Framework 3.5를 대상으로 하는 Office 솔루션을 배포한 다음 프로젝트 대상을 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경하는 경우 다시 게시한 후 최종 사용자가 솔루션을 제거하고 다시 설치해야 합니다. 대상이 변경 된 솔루션을 다시 게시 하 고 최종 사용자 컴퓨터에서 솔루션이 업데이트 되는 경우 최종 사용자는 업데이트 된 솔루션을 실행할 때을 받게 됩니다 <xref:System.Runtime.InteropServices.COMException> .

## <a name="see-also"></a>참고 항목
- [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)