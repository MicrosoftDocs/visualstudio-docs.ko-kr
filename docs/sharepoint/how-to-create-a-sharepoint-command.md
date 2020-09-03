---
title: '방법: SharePoint 명령 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 15ea7ff86e90bf7a474f9d64c30a9803e3e20bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016214"
---
# <a name="how-to-create-a-sharepoint-command"></a>방법: SharePoint 명령 만들기
  SharePoint 도구 확장에서 서버 개체 모델을 사용 하려면 API를 호출 하는 사용자 지정 *SharePoint 명령을* 만들어야 합니다. 서버 개체 모델을 직접 호출할 수 있는 어셈블리에서 SharePoint 명령을 정의 합니다.

 SharePoint 명령의 용도에 대 한 자세한 내용은 [sharepoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.

### <a name="to-create-a-sharepoint-command"></a>SharePoint 명령을 만들려면

1. 다음 구성이 포함 된 클래스 라이브러리 프로젝트를 만듭니다.

    - .NET Framework 3.5를 대상으로 합니다. 대상 프레임 워크를 선택 하는 방법에 대 한 자세한 내용은 [방법: 한 버전의 .NET Framework을 대상으로 하는 방법](../ide/visual-studio-multi-targeting-overview.md)을 참조 하세요.

    - 는 AnyCPU 또는 x64 플랫폼을 대상으로 합니다. 기본적으로 클래스 라이브러리 프로젝트의 대상 플랫폼은 AnyCPU입니다. 대상 플랫폼을 선택 하는 방법에 대 한 자세한 내용은 [방법: 플랫폼을 대상으로 하는 프로젝트 구성](../ide/how-to-configure-projects-to-target-platforms.md)을 참조 하세요.

    > [!NOTE]
    > Sharepoint 명령 대상 .NET Framework 3.5 및 SharePoint 도구 확장을 대상으로 하는 sharepoint 명령은를 대상으로 하기 때문에 sharepoint 도구 확장을 정의 하는 동일한 프로젝트에서 SharePoint 명령을 구현할 수 없습니다 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . 확장에서 사용 하는 SharePoint 명령을 별도의 프로젝트에 정의 해야 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - VisualStudio.

    - Microsoft SharePoint

3. 프로젝트의 클래스에서 SharePoint 명령을 정의 하는 메서드를 만듭니다. 메서드는 다음 지침을 따라야 합니다.

    - 하나 또는 두 개의 매개 변수를 사용할 수 있습니다.

         첫 번째 매개 변수는 개체 여야 합니다 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> . 이 개체는 명령이 실행 되는 Microsoft. SharePoint. m a m. 또한 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> Visual Studio의 **출력** 창 또는 **오류 목록** 창에 메시지를 쓰는 데 사용할 수 있는 개체를 제공 합니다.

         두 번째 매개 변수는 사용자가 선택한 형식일 수 있지만이 매개 변수는 선택 사항입니다. SharePoint 도구 확장의 데이터를 명령에 전달 해야 하는 경우 SharePoint 명령에이 매개 변수를 추가할 수 있습니다.

    - 반환 값을 가질 수 있지만이는 선택 사항입니다.

    - 두 번째 매개 변수와 반환 값은 WCF (Windows Communication Foundation)에서 serialize 할 수 있는 형식 이어야 합니다. 자세한 내용은 [데이터 계약 Serializer에서 지 원하는 형식](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) 및 [XmlSerializer 클래스 사용](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)을 참조 하세요.

    - 메서드는 모든 표시 유형 (**public**, **internal**또는 **private**)을 가질 수 있으며 정적 또는 비정적 일 수 있습니다.

4. 을 메서드에 적용 합니다 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> . 이 특성은 명령의 고유 식별자를 지정 합니다. 이 식별자는 메서드 이름과 일치 하지 않아도 됩니다.

     SharePoint 도구 확장에서 명령을 호출 하는 경우에는 동일한 고유 식별자를 지정 해야 합니다. 자세한 내용은 [방법: SharePoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)을 참조 하세요.

## <a name="example"></a>예
 다음 코드 예제에서는 식별자를 포함 하는 SharePoint 명령을 보여 줍니다 `Contoso.Commands.UpgradeSolution` . 이 명령은 서버 개체 모델의 Api를 사용 하 여 배포 된 솔루션으로 업그레이드 합니다.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 암시적 첫 번째 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수 외에도이 명령에는 SharePoint 사이트로 업그레이드 되는 .wsp 파일의 전체 경로를 포함 하는 사용자 지정 문자열 매개 변수가 있습니다. 큰 예제의 컨텍스트에서이 코드를 보려면 [연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)를 참조 하세요.

## <a name="compiling-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio.

- Microsoft SharePoint

## <a name="deploying-the-command"></a>명령 배포
 명령을 배포 하려면 명령을 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 사용 하는 확장 어셈블리를 사용 하 여 동일한 확장 (*vsix*) 패키지에 명령 어셈블리를 포함 합니다. 또한 source.extension.vsixmanifest 파일에서 명령 어셈블리에 대 한 항목을 추가 해야 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [방법: SharePoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
