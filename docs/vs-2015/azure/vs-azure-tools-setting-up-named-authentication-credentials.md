---
title: 명명된 인증 자격 증명 설정 | Microsoft Docs
description: 애플리케이션을 Visual Studio에서 Azure로 게시하거나 기존 클라우드 서비스를 모니터링할 수 있도록 Visual Studio가 Azure에 대한 요청을 인증하는 데 사용할 수 있는 자격 증명을 제공하는 방법에 대해 알아봅니다.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 27837390306ad29da55c7c5262ecd8fa6bcf75b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917372"
---
# <a name="set-up-named-authentication-credentials"></a>명명된 인증 자격 증명 설정

Azure에 애플리케이션을 게시하거나 기존 클라우드 서비스를 모니터링하려면 Visual Studio에서 Azure에 대한 요청을 인증하기 위한 자격 증명, 즉 Azure 구독 ID 및 2,048비트 이상의 키가 있는 유효한 X.509 v3 인증서가 필요합니다. 다음 방법 중 하나를 사용하여 이러한 자격 증명을 제공합니다.

- Visual Studio에서 **보기> 서버 탐색기**를 차례로 선택하고, **Azure** 노드를 마우스 오른쪽 단추로 클릭하고, **Microsoft Azure 구독에 연결**을 선택한 다음, 로그인합니다.
- 인증서에 대한 공개 키가 포함된 구독 파일(`.publishsettings`)을 만듭니다. 이 문서에서 설명한 대로 구독 파일에는 둘 이상의 구독에 대한 자격 증명이 포함될 수 있습니다.

참고: 이러한 자격 증명은 Azure Storage 서비스에 대한 요청을 인증하는 데 사용되는 자격 증명과 다릅니다.

## <a name="create-a-subscription-file"></a>구독 파일 만들기

[서버 탐색기]에서 **Azure** 노드를 마우스 오른쪽 단추로 클릭하고 **구독 관리 및 필터링**을 선택합니다. 그런 다음 **인증서** 탭을 선택하고 다음 작업 중 하나를 수행합니다.

- **가져오기**를 선택하여 **Microsoft Azure 구독 가져오기** 대화 상자를 엽니다. **구독 파일 다운로드** 링크를 선택하고, 브라우저에서 다운로드한 파일을 임시 위치에 저장합니다. 대화 상자에서 다운로드 위치를 다시 찾은 다음 인증에 사용할 수 있도록 가져옵니다.
- 활성 구독을 선택하고 **편집**을 선택합니다. 그러면 인증에 사용할 기존 구독을 편집하는 대화 상자가 열립니다.
- **새로 만들기**를 선택하여 **새 구독** 대화 상자를 열고 필요한 세부 정보를 제공합니다. 클라우드 서비스에 인증서를 업로드하려면 Azure Portal에 로그인하고, 클라우드 서비스로 이동하고, **설정 > 관리 인증서**를 차례로 선택하고, **업로드**를 선택한 다음, `.cer` 파일에 대한 경로를 지정합니다.

인증서를 직접 만들려면 [Azure에 대한 관리 인증서 만들기 및 업로드](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx)의 지침을 참조한 다음, 인증서를 [Azure Portal](https://portal.azure.com/)에 수동으로 업로드합니다.

## <a name="next-steps"></a>다음 단계

- [웹앱의 일반적인 개요](/azure/app-service/)
- [Azure App Service에 앱 배포](/azure/app-service/app-service-deploy-local-git) 
- [Visual Studio를 사용하여 WebJob 배포](/azure/app-service/websites-dotnet-deploy-webjobs)
- [클라우드 서비스 만들기 및 배포](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)