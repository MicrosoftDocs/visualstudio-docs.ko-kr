---
title: Azure 클라우드 서비스에 대한 역할 구성
description: Visual Studio를 사용하여 Azure 클라우드 서비스에 대한 역할을 설정하고 구성하는 방법에 대해 알아봅니다.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 6f05f97155427d75b88bb509a6bfb09644d8c686
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250854"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Visual Studio를 사용하여 Azure 클라우드 서비스 역할 구성
Azure 클라우드 서비스에는 하나 이상의 작업자 또는 웹 역할이 포함될 수 있습니다. 각 역할에 대해 해당 역할을 설정하는 방법을 정의하고 해당 역할을 실행하는 방법을 구성해야 합니다. 클라우드 서비스의 역할에 대한 자세한 내용은 [Azure Cloud Services 소개](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services)를 참조하세요.

클라우드 서비스에 대한 정보는 다음 파일에 저장됩니다.

- **Servicedefinition. .csdef** -서비스 정의 파일은 필요한 역할, 끝점 및 가상 컴퓨터 크기를 포함 하 여 클라우드 서비스에 대 한 런타임 설정을 정의 합니다. 역할이 실행 중일 때 `ServiceDefinition.csdef`에 저장된 데이터는 변경할 수 없습니다.
- **ServiceConfiguration.cscfg** - 서비스 구성 파일은 실행되는 역할의 인스턴스 수와 역할에 대해 정의된 설정 값을 구성합니다. 역할이 실행 중인 동안 `ServiceConfiguration.cscfg`에 저장된 데이터는 변경할 수 있습니다.

역할 실행 방법을 제어하는 설정에 대해 다른 값을 저장하기 위해 여러 서비스 구성을 정의할 수 있습니다. 각 배포 환경에 대해 서로 다른 서비스 구성을 사용할 수 있습니다. 예를 들어 스토리지 계정 연결 문자열을 설정하여 로컬 서비스 구성에서 로컬 Azure Storage 에뮬레이터를 사용하고, 다른 서비스 구성을 만들어 클라우드에서 Azure Storage를 사용할 수 있습니다.

Visual Studio에서 Azure 클라우드 서비스를 만들 때 두 개의 서비스 구성을 자동으로 만들어 Azure 프로젝트에 추가합니다.

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Azure 클라우드 서비스 구성
다음 단계와 같이 Visual Studio의 [솔루션 탐색기]에서 Azure 클라우드 서비스를 구성할 수 있습니다.

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **속성**을 선택합니다.

    ![솔루션 탐색기 프로젝트 - 상황에 맞는 메뉴](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. 프로젝트 속성 페이지에서 **개발** 탭을 선택합니다.

    ![프로젝트 속성 페이지 - 개발 탭](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. **서비스 구성** 목록에서 편집할 서비스 구성의 이름을 선택합니다. 이 역할에 대한 서비스 구성을 모두 변경하려면 **모든 구성**을 선택합니다.

    > [!IMPORTANT]
    > 특정 서비스 구성을 선택하면 일부 속성은 모든 구성에 대해서만 설정 가능하므로 비활성화됩니다. 이러한 속성을 편집하려면 **모든 구성**을 선택해야 합니다.

    ![Azure 클라우드 서비스에 대한 서비스 구성 목록](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>역할 인스턴스 수 변경
클라우드 서비스의 성능을 개선하기 위해 실행 중인 역할의 인스턴스 수를 사용자 수 또는 특정 역할에 대해 예상되는 부하에 따라 변경할 수 있습니다. Azure에서 클라우드 서비스를 실행하는 경우 별도의 가상 머신이 역할의 각 인스턴스에 대해 생성됩니다. 이렇게 하면 이 클라우드 서비스의 배포에 대한 청구에 영향을 줍니다. 대금 청구에 대한 자세한 내용은 [Microsoft Azure 청구서 이해](/azure/billing/billing-understand-your-bill)를 참조하세요.

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 확장 합니다. **역할** 노드에서 업데이트하려는 역할을 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **속성**을 선택합니다.

    ![솔루션 탐색기 - Azure 역할의 상황에 맞는 메뉴](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **구성** 탭을 선택합니다.

    ![구성 탭](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. **서비스 구성** 목록에서 업데이트할 서비스 구성을 선택합니다.

    ![서비스 구성 목록](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. **인스턴스 수** 텍스트 상자에서 이 역할에 대해 시작하려는 인스턴스 수를 입력합니다. Azure에 클라우드 서비스를 게시할 때 각 인스턴스는 별도의 가상 머신에서 실행됩니다.

    ![인스턴스 수 업데이트](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Visual Studio의 도구 모음에서 **저장**을 선택 합니다.

## <a name="manage-connection-strings-for-storage-accounts"></a>스토리지 계정에 대한 연결 문자열 관리
서비스 구성에 대한 연결 문자열을 추가, 제거 또는 수정할 수 있습니다. 예를 들어, `UseDevelopmentStorage=true`값이 있는 로컬 서비스 구성에 대해 로컬 연결 문자열이 필요할 수 있습니다. 또한 Azure에서 스토리지 계정을 사용하는 클라우드 서비스 구성을 구성하려고 할 수도 있습니다.

> [!WARNING]
> 스토리지 계정 연결 문자열에 대해 Azure Storage 계정 키 정보를 입력하면 이 정보가 서비스 구성 파일에 로컬로 저장됩니다. 그러나 현재는 이 정보가 암호화된 텍스트로 저장되지 않습니다.
>
>

각 서비스 구성에 대해 서로 다른 값을 사용하면 클라우드 서비스에서 서로 다른 연결 문자열을 사용하거나 클라우드 서비스에서 Azure로 게시할 때 코드를 수정하지 않아도 됩니다. 코드에서 연결 문자열에 동일한 이름을 사용할 수 있으며, 해당 값은 클라우드 서비스를 빌드하거나 게시할 때 선택하는 서비스 구성에 따라 다릅니다.

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 확장 합니다. **역할** 노드에서 업데이트하려는 역할을 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **속성**을 선택합니다.

    ![솔루션 탐색기 - Azure 역할의 상황에 맞는 메뉴](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **설정** 탭을 선택합니다.

    ![설정 탭](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **서비스 구성** 목록에서 업데이트할 서비스 구성을 선택합니다.

    ![서비스 구성](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. 연결 문자열을 추가하려면 **설정 추가**를 선택합니다.

    ![연결 문자열 추가](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. 새 설정이 목록에 추가되면 목록의 행을 필요한 정보로 업데이트합니다.

    ![새 연결 문자열](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **이름** - 연결 문자열에 사용할 이름을 입력합니다.
    - **형식** - 드롭다운 목록에서 **연결 문자열**을 선택합니다.
    - **값** - **값** 셀에 연결 문자열을 직접 입력하거나 **스토리지 연결 문자열 만들기** 대화 상자에서 줄임표(...)를 선택하여 작업할 수 있습니다.

1. **스토리지 연결 문자열 만들기** 대화 상자에서 **다음을 사용하여 연결** 옵션을 선택합니다. 그런 다음 선택한 옵션에 대한 지침을 따릅니다.

    - **Microsoft Azure Storage 에뮬레이터** -이 옵션을 선택 하는 경우 Azure에만 적용 되므로 대화 상자의 나머지 설정은 사용할 수 없습니다. **확인**을 선택합니다.
    - **구독** - 이 옵션을 선택하면 드롭다운 목록을 사용하여 Microsoft 계정을 선택하고 로그인하거나 Microsoft 계정을 추가합니다. Azure 구독 및 스토리지 계정을 선택합니다. **확인**을 선택합니다.
    - **수동으로 입력한 자격 증명** - 스토리지 계정 이름과 기본 또는 보조 키를 입력합니다. **연결** 에 대 한 옵션을 선택 합니다. 대부분의 시나리오에는 HTTPS를 권장 합니다. **확인을**선택 합니다.

1. 연결 문자열을 삭제하려면 연결 문자열을 선택한 다음 **설정 제거**를 선택합니다.

1. Visual Studio의 도구 모음에서 **저장**을 선택 합니다.

## <a name="programmatically-access-a-connection-string"></a>프로그래밍 방식으로 연결 문자열 액세스

다음 단계에서는 C#을 사용하여 연결 문자열에 프로그래밍 방식으로 액세스하는 방법을 보여 줍니다.

1. 설정을 사용할 C# 파일에 다음 using 지시문을 추가합니다.

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. 다음 코드는 연결 문자열에 액세스하는 방법의 예제를 보여 줍니다. &lt;ConnectionStringName> 자리 표시자를 적절한 값으로 바꿉니다.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Azure 클라우드 서비스에서 사용할 사용자 지정 설정 추가
서비스 구성 파일의 사용자 지정 설정을 통해 특정 서비스 구성에 대한 문자열의 이름 및 값을 추가할 수 있습니다. 설정 값을 읽고 이 값을 코드에서 논리를 제어하는 데 사용하여 클라우드 서비스에서 기능을 구성하는 데 이 설정을 사용하도록 선택할 수 있습니다. 서비스 패키지를 다시 빌드하지 않고 클라우드 서비스가 실행 중인 경우에도 이러한 서비스 구성 값을 변경할 수 있습니다. 설정이 변경될 때 코드에서 알림을 확인할 수 있습니다. [RoleEnvironment.Changing 이벤트](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx)를 참조하세요.

서비스 구성에 대한 사용자 지정 설정을 추가, 제거 또는 수정할 수 있습니다. 다양한 서비스 구성에 대해 이러한 문자열에 서로 다른 값이 필요할 수 있습니다.

각 서비스 구성에 대해 서로 다른 값을 사용하면 클라우드 서비스에서 서로 다른 문자열을 사용하거나 클라우드 서비스에서 Azure로 게시할 때 코드를 수정하지 않아도 됩니다. 코드에서 문자열에 동일한 이름을 사용할 수 있으며, 해당 값은 클라우드 서비스를 빌드하거나 게시할 때 선택하는 서비스 구성에 따라 다릅니다.

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 확장 합니다. **역할** 노드에서 업데이트하려는 역할을 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **속성**을 선택합니다.

    ![솔루션 탐색기 - Azure 역할의 상황에 맞는 메뉴](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **설정** 탭을 선택합니다.

    ![설정 탭](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **서비스 구성** 목록에서 업데이트할 서비스 구성을 선택합니다.

    ![서비스 구성 목록](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. 사용자 지정 설정을 추가하려면 **설정 추가**를 선택합니다.

    ![사용자 지정 설정 추가](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. 새 설정이 목록에 추가되면 목록의 행을 필요한 정보로 업데이트합니다.

    ![새 사용자 지정 설정](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **이름** - 설정 이름을 입력합니다.
    - **형식** - 드롭다운 목록에서 **문자열**을 선택합니다.
    - **값** - 설정 값을 입력합니다. 값을 **값** 셀에 값을 직접 입력하거나 줄임표(...)를 선택하여 **문자열 편집** 대화 상자에서 값을 입력할 수 있습니다.

1. 사용자 지정 설정을 삭제하려면 설정을 선택한 다음 **설정 제거**를 선택합니다.

1. Visual Studio의 도구 모음에서 **저장**을 선택 합니다.

## <a name="programmatically-access-a-custom-settings-value"></a>프로그래밍 방식으로 사용자 지정 설정 값 액세스

다음 단계에서는 C#을 사용하여 사용자 지정 설정에 프로그래밍 방식으로 액세스하는 방법을 보여 줍니다.

1. 설정을 사용할 C# 파일에 다음 using 지시문을 추가합니다.

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. 다음 코드는 사용자 지정 설정에 액세스하는 방법의 예제를 보여 줍니다. &lt;SettingName> 자리 표시자를 적절한 값으로 바꿉니다.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>각 역할 인스턴스에 대한 로컬 스토리지 관리
각 역할 인스턴스에 대한 로컬 파일 시스템 스토리지를 추가할 수 있습니다. 해당 스토리지에 저장된 데이터는 데이터가 저장된 역할의 다른 인스턴스 또는 다른 역할에서 액세스할 수 없습니다.

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 확장 합니다. **역할** 노드에서 업데이트하려는 역할을 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **속성**을 선택합니다.

    ![솔루션 탐색기 - Azure 역할의 상황에 맞는 메뉴](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **로컬 스토리지** 탭을 선택합니다.

    ![로컬 스토리지 탭](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. **서비스 구성** 목록에서 모든 서비스 구성에 로컬 스토리지 설정이 적용되므로 **모든 구성**이 선택되어 있는지 확인합니다. 다른 값을 지정하면 페이지의 모든 입력 필드가 비활성화됩니다.

    ![서비스 구성 목록](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. 로컬 스토리지 항목을 추가하려면 **로컬 스토리지 추가**를 선택합니다.

    ![로컬 스토리지 추가](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. 새 로컬 스토리지 항목이 목록에 추가되면 목록의 행을 필요한 정보로 업데이트합니다.

    ![새 로컬 스토리지 항목](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **이름** - 새 로컬 스토리지에 사용할 이름을 입력합니다.
    - **크기(MB)** - 새 로컬 스토리지에 필요한 크기(MB)를 입력합니다.
    - **역할 재생에서 정리** - 이 옵션을 선택하면 역할에 대한 가상 머신을 재활용할 때 새 로컬 스토리지의 데이터를 제거합니다.

1. 로컬 스토리지 항목을 삭제하려면 해당 항목을 선택한 다음 **로컬 스토리지 제거**를 선택합니다.

1. Visual Studio의 도구 모음에서 **저장**을 선택 합니다.

## <a name="programmatically-accessing-local-storage"></a>프로그래밍 방식으로 로컬 스토리지 액세스

이 섹션에서는 `MyLocalStorageTest.txt` 테스트 텍스트 파일을 작성하여 C#을 통해 로컬 스토리지에 프로그래밍 방식으로 액세스하는 방법을 보여 줍니다.

### <a name="write-a-text-file-to-local-storage"></a>로컬 스토리지에 텍스트 파일 작성

다음 코드는 로컬 스토리지에 텍스트 파일을 작성하는 방법의 예제를 보여 줍니다. &lt;LocalStorageName> 자리 표시자를 적절한 값으로 바꿉니다.

```csharp
// Retrieve an object that points to the local storage resource
LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");

//Define the file name and path
string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
String filePath = Path.Combine(paths);

using (FileStream writeStream = File.Create(filePath))
{
    Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
    writeStream.Write(textToWrite, 0, textToWrite.Length);
}
```

### <a name="find-a-file-written-to-local-storage"></a>로컬 스토리지에 기록된 파일 찾기

이전 섹션의 코드로 만든 파일을 보려면 다음 단계를 수행합니다.

1. Windows 알림 영역에서 Azure 아이콘을 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **컴퓨팅 에뮬레이터 UI 표시**를 선택합니다.

    ![Azure 컴퓨팅 에뮬레이터 표시](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. 웹 역할을 선택합니다.

    ![Azure 컴퓨팅 에뮬레이터](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. **Microsoft Azure Compute 에뮬레이터** 메뉴에서 **도구** > **로컬 저장소 열기**를 선택합니다.

    ![로컬 저장소 메뉴 항목 열기](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Windows 탐색기 창이 열리면 **검색** 텍스트 상자에서 'MyLocalStorageTest.txt'를 입력하고 **Enter** 키를 눌러 검색을 시작합니다.

## <a name="next-steps"></a>다음 단계
[Azure 프로젝트 구성](vs-azure-tools-configuring-an-azure-project.md)을 읽고 Visual Studio에서 Azure 프로젝트에 대해 자세히 알아봅니다. [스키마 참조](https://msdn.microsoft.com/library/azure/dd179398)를 읽고 클라우드 서비스 스키마에 대해 자세히 알아봅니다.
