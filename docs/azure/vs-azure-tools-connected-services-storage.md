---
title: 연결된 서비스를 사용하여 Azure Storage 추가 | Microsoft Docs
description: Visual Studio를 사용 하 여 Azure Storage 서비스 종속성을 앱에 추가 연결된 서비스
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: 4a1b7bcc8b95b30ea3737dc2561c5abb280e2b5c
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88639456"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio 연결 서비스를 사용하여 Azure Storage 추가

Visual Studio를 사용 하 여 다음 중 하나를 **연결된 서비스** 기능을 사용 하 여 Azure Storage에 연결할 수 있습니다.

- .NET Framework 콘솔 앱
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (콘솔 앱, WPF, Windows Forms, 클래스 라이브러리 포함)
- .NET Core 작업자 역할
- Azure 기능
- 유니버설 Windows 플랫폼 앱
- Xamarin
- Cordova

연결된 서비스 기능은 필요한 모든 참조와 연결 코드를 프로젝트에 추가하고 구성 파일을 적절하게 수정합니다.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 연결된 서비스](/visualstudio/mac/connected-services)를 참조하세요.
## <a name="prerequisites"></a>사전 요구 사항

- Azure 워크 로드가 설치 된 Visual Studio
- 지원 되는 형식 중 하나에 해당 하는 프로젝트

## <a name="connect-to-azure-storage-using-connected-services"></a>연결된 서비스를 사용 하 여 Azure Storage에 연결

::: moniker range="vs-2017"

1. Visual Studio에서 프로젝트를 엽니다.

1. **솔루션 탐색기**에서 **연결된 서비스** 노드를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **연결 된 서비스 추가**를 선택 합니다.

    ![Azure 연결된 서비스 추가](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. **연결된 서비스** 페이지에서 **Azure Storage의 클라우드 스토리지**를 선택합니다.

    ![Azure Storage 추가](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. **Azure Storage** 대화 상자에서, 기존 스토리지 계정을 선택한 다음 **추가**를 선택합니다.

    스토리지 계정을 만들어야 하는 경우 다음 단계로 이동합니다. 그렇지 않을 경우 6단계로 건너뜁니다.

    ![프로젝트에 기존 스토리지 계정 추가](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. 스토리지 계정을 만들려면

   1. 대화 상자 아래쪽에 있는 **새 Storage 계정 만들기**를 선택합니다.

   1. **Storage 계정 만들기** 대화 상자를 채운 다음 **만들기**를 선택합니다.

       ![새 Azure Storage 계정](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. **Azure Storage** 대화 상자가 표시되면 새 스토리지 계정이 목록에 나타납니다. 목록에서 새 스토리지 계정을 선택하고 **추가**를 선택합니다.

1. 연결된 스토리지 서비스가 프로젝트의 **서비스 참조** 노드 아래에 나타납니다.
:::moniker-end

:::moniker range=">=vs-2019"

1. Visual Studio에서 프로젝트를 엽니다.

1. **솔루션 탐색기**에서 **연결된 서비스** 노드를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **연결 된 서비스 추가**를 선택 합니다.

    ![Azure 연결된 서비스 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. **연결된 서비스** 탭에서 **서비스 종속성**에 대 한 + 아이콘을 선택 합니다.

    ![서비스 종속성 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **종속성 추가** 페이지에서 **Azure Storage**를 선택 합니다.

    ![Azure Storage 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    아직 로그인 하지 않은 경우 Azure 계정에 로그인 합니다. Azure 계정이 없으면 [무료 평가판](https://azure.microsoft.com/account/free)에 등록할 수 있습니다.

1. **Azure Storage 구성** 화면에서 기존 저장소 계정을 선택 하 고 **다음**을 선택 합니다.

    스토리지 계정을 만들어야 하는 경우 다음 단계로 이동합니다. 그렇지 않을 경우 6단계로 건너뜁니다.

    ![프로젝트에 기존 스토리지 계정 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. 스토리지 계정을 만들려면

   1. 대화 상자 아래쪽에서 **저장소 계정 만들기** 를 선택 합니다.

   1. 새 대화 상자 **만들기 Azure Storage** 를 입력 하 고 **만들기**를 선택 합니다.

       ![새 Azure Storage 계정](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. **Azure Storage** 대화 상자가 표시되면 새 스토리지 계정이 목록에 나타납니다. 목록에서 새 저장소 계정을 선택 하 고 **다음**을 선택 합니다.

1. 연결 문자열 이름을 입력 하 고 연결 문자열을 로컬 비밀 파일에 저장할지, 아니면 [Azure Key Vault](/azure/key-vault)에 저장할지를 선택 합니다.

   ![연결 문자열 지정](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. **변경 내용 요약** 화면에는 프로세스를 완료 한 경우 프로젝트에 적용 되는 모든 수정 사항이 표시 됩니다. 변경 내용이 양호 하면 **마침**을 선택 합니다.

   ![변경 내용 요약](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. 연결된 스토리지 서비스가 프로젝트의 **서비스 참조** 노드 아래에 나타납니다.
:::moniker-end

## <a name="see-also"></a>참고 항목

- [Azure Storage 포럼](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Azure Storage 설명서](/azure/storage/)
- [연결된 서비스(Mac용 Visual Studio)](/visualstudio/mac/connected-services)
