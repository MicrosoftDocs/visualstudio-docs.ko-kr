---
title: SharePoint 개체 모델 호출 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62988403"
---
# <a name="call-into-the-sharepoint-object-models"></a>SharePoint 개체 모델 호출
  Visual Studio에서 SharePoint 도구에 대 한 확장을 만들 때 특정 작업을 수행 하려면 SharePoint Api를 호출 해야 할 수 있습니다. 예를 들어 SharePoint 프로젝트에 대 한 사용자 지정 배포 단계를 만드는 경우 솔루션을 배포 하는 일부 작업을 수행 하기 위해 SharePoint Api를 호출 해야 할 수 있습니다.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 및는 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] SharePoint 도구 확장에서 사용할 수 있는 두 가지 개체 모델, 즉 서버 개체 모델과 클라이언트 개체 모델을 제공 합니다. 각 개체 모델은 SharePoint 도구 확장의 컨텍스트에서 장단점이 있습니다.

 SharePoint 개체 모델의 개요는 [sharepoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)를 참조 하세요.

## <a name="use-the-client-object-model-in-extension-projects"></a>확장 프로젝트에서 클라이언트 개체 모델 사용
 SharePoint 도구에 대 한 확장을 개발 하는 경우 다른 관리 되는 Api 집합과 마찬가지로 프로젝트에서 클라이언트 개체 모델을 사용할 수 있습니다. 클라이언트 개체 모델의 어셈블리에 대 한 참조를 프로젝트에 추가할 수 있으며, 사용자 코드에서 직접 클라이언트 개체 모델의 Api를 호출할 수 있습니다.

 그러나 클라이언트 개체 모델은 SharePoint 도구 확장의 컨텍스트에서 다음과 같은 두 가지 단점이 있습니다.

- 클라이언트 개체 모델은 서버 개체 모델의 하위 집합만 제공 합니다. 클라이언트 개체 모델에 노출 되지 않은 SharePoint 기능을 사용 해야 하는 경우 서버 개체 모델을 사용 해야 합니다.

- 대부분의 경우 SharePoint 도구 확장에서 클라이언트 개체 모델을 사용 하는 것이 좋지만 클라이언트 개체 모델 호출이 예상 대로 작동 하지 않는 몇 가지 시나리오가 발생할 수 있습니다. 클라이언트 개체 모델은 클라이언트 응용 프로그램에서 원격 서버 또는 팜의 SharePoint 사이트를 호출 하는 데 사용 하도록 설계 되었습니다. Visual Studio의 SharePoint 도구는 개발 컴퓨터에 로컬 SharePoint를 설치한 경우에만 작동 합니다. 따라서 SharePoint 도구 확장에서 클라이언트 개체 모델을 사용 하는 경우 클라이언트 개체 모델이 사용 되도록 디자인 된 방법이 아닌 로컬 컴퓨터에서 SharePoint 사이트를 호출 합니다.

  Visual Studio의 SharePoint 도구 확장에서 클라이언트 개체 모델을 사용 하는 방법을 보여 주는 연습은 [연습: 서버 탐색기 확장에서 sharepoint 클라이언트 개체 모델 호출](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)을 참조 하세요.

## <a name="use-the-server-object-model-in-extension-projects"></a>확장 프로젝트에서 서버 개체 모델 사용
 서버 개체 모델은 클라이언트 개체 모델의 상위 집합입니다. 서버 개체 모델을 사용 하는 경우 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 및에서 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 프로그래밍 방식으로 노출 하는 모든 기능을 사용할 수 있습니다.

 SharePoint 도구 확장은 서버 개체 모델의 Api를 사용할 수 있지만 Api를 직접 호출할 수는 없습니다. 서버 개체 모델은 .NET Framework 3.5를 대상으로 하는 64 비트 프로세스 에서만 호출할 수 있습니다. 그러나 SharePoint 도구 확장에는가 필요 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 하며 32 비트 Visual Studio 프로세스에서 실행 됩니다. 이렇게 하면 SharePoint 도구 확장에서 SharePoint 서버 개체 모델의 어셈블리를 직접 참조할 수 없습니다.

 SharePoint 도구 확장에서 서버 개체 모델을 사용 하려면 API를 호출 하는 사용자 지정 *SharePoint 명령을* 만들어야 합니다. 서버 개체 모델을 직접 호출할 수 있는 보조 어셈블리에서 SharePoint 명령을 정의 합니다. 확장 프로젝트에서 개체의 ExecuteCommand 메서드를 사용 하 여 SharePoint 명령을 간접적으로 호출 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> .

 SharePoint 명령을 만들고 사용 하는 방법에 대 한 자세한 내용은 [방법: sharepoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md) 및 [방법: sharepoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)을 참조 하세요. SharePoint 명령을 배포 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 sharepoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

 SharePoint 명령을 만들고 사용 하는 방법을 보여 주는 연습은 [연습: sharepoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) 및 [연습: 웹 파트 표시를 위한 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)을 참조 하세요.

### <a name="understand-how-sharepoint-commands-are-executed"></a>SharePoint 명령 실행 방법 이해
 SharePoint 명령을 정의 하는 어셈블리는 *vssphost4.exe*라는 64 비트 호스트 프로세스에 로드 됩니다. SharePoint 도구 확장에서 SharePoint 명령을 호출한 후에는 32 비트 Visual Studio 프로세스 (*devenv.exe*) 대신 *vssphost4.exe* 에서 명령이 실행 됩니다. 레지스트리의 값을 설정 하 여 SharePoint 명령이 실행 되는 방법의 일부 측면을 제어할 수 있습니다. 자세한 내용은 [Visual Studio의 SharePoint 도구에 대 한 디버그 확장](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)(영문)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)
- [방법: SharePoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [SharePoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
