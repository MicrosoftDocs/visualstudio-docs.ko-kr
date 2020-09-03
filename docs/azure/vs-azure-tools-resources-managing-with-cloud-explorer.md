---
title: 클라우드 탐색기를 사용하여 Azure 리소스 관리 | Microsoft Docs
description: 클라우드 탐색기를 사용하여 Visual Studio 내에서 Azure 리소스를 검색 및 관리하는 방법에 대해 알아봅니다.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 175aa7111d77e92fb29a3983db7365e068abba2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800387"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Visual Studio 클라우드 탐색기에서 Azure 계정과 연결된 리소스 관리

클라우드 탐색기를 사용하여 Azure 리소스 및 리소스 그룹을 보고, 해당 속성을 검사하고, Visual Studio 내에서 핵심 개발자 진단 작업을 수행할 수 있습니다.

[Azure Portal](https://portal.azure.com)에서와 마찬가지로 클라우드 탐색기는 Azure Resource Manager 스택을 토대로 구축되었습니다. 따라서 클라우드 탐색기는 Azure 리소스 그룹과 같은 리소스 및 논리 앱과 API 앱과 같은 Azure 서비스를 이해하고 RBAC([역할 기반 액세스 제어](/azure/role-based-access-control/role-assignments-portal))를 지원합니다.

## <a name="prerequisites"></a>필수 구성 요소

* **Azure 워크로드**가 선택된 Visual Studio 2017 이상([Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 참조). [.NET용 Microsoft Azure SDK 2.9](https://www.microsoft.com/download/details.aspx?id=51657)가 포함된 이전 버전의 Visual Studio를 사용할 수도 있습니다.
* Microsoft Azure 계정 - 계정이 없는 경우 [평가판을 등록](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)하거나 [Visual Studio 구독자 혜택을 활성화](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)할 수 있습니다.

> [!NOTE]
> 클라우드 탐색기를 보려면 **Ctrl** + **Q** 를 눌러 검색 상자를 활성화 한 다음 **클라우드 탐색기**을 입력 합니다.

## <a name="add-an-azure-account-to-cloud-explorer"></a>클라우드 탐색기에 Azure 계정 추가

Azure 계정과 연결 된 리소스를 보려면 먼저 **클라우드 탐색기**에 계정을 추가 해야 합니다.

1. **클라우드 탐색기**에서 **계정 관리** 단추를 선택 합니다.

   ![클라우드 탐색기 Azure 계정 설정 아이콘](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. **계정 관리**를 선택합니다.

   ![클라우드 탐색기 계정 추가 링크](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. 해당 리소스를 검색하려는 Azure 계정에 로그인합니다.

1. Azure 계정에 로그인하면 해당 계정과 연결된 구독이 표시됩니다. 탐색할 계정 구독에 대한 확인란을 선택한 다음 **적용**을 선택합니다.

   ![클라우드 탐색기: 표시할 Azure 구독 선택](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. 검색 하려는 리소스를 포함 하는 구독을 선택 하면 해당 구독과 리소스가 **클라우드 탐색기**표시 됩니다.

   ![Azure 계정에 대한 클라우드 탐색기 리소스 목록](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>클라우드 탐색기에서 Azure 계정 제거

1. **클라우드 탐색기**에서 **계정 관리**를 선택합니다.

   ![클라우드 탐색기 Azure 계정 설정 아이콘](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. 제거할 계정 옆에 있는 **계정 관리**를 선택합니다.

   ![클라우드 탐색기 Azure 계정 설정 아이콘](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. **제거**를 선택하여 계정을 제거합니다.

    ![클라우드 탐색기 계정 관리 대화 상자](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>리소스 종류 또는 리소스 그룹 보기

Azure 리소스를 보려면 **리소스 종류** 또는 **리소스 그룹** 보기를 선택할 수 있습니다.

1. **클라우드 탐색기**에서 리소스 보기 드롭다운을 선택합니다.

   ![원하는 리소스 보기를 선택하기 위한 클라우드 탐색기 드롭다운 목록](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. 상황에 맞는 메뉴에서 원하는 보기를 선택합니다.

   * **리소스 종류** 보기 - [Azure Portal](https://portal.azure.com)에서 사용되는 일반적인 보기로, 웹앱, 스토리지 계정 및 가상 머신과 같은 형식으로 분류된 Azure 리소스를 보여 줍니다.
   * **리소스 그룹** 보기 - 연관된 Azure 리소스 그룹으로 Azure 리소스를 분류합니다. 리소스 그룹은 일반적으로 특정 애플리케이션에서 사용되는 Azure 리소스 번들입니다. Azure 리소스 그룹에 대한 자세한 내용은 [Azure Resource Manager 개요](/azure/azure-resource-manager/resource-group-overview)를 참조하세요.

   다음 이미지는 두 리소스 보기를 비교해서 보여 줍니다.

   ![클라우드 탐색기 리소스 보기 비교](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>클라우드 탐색기에서 리소스 보기 및 탐색

클라우드 탐색기에서 Azure 리소스를 탐색하고 정보를 보려면, 항목의 형식 또는 연결된 리소스 그룹을 확장한 다음 리소스를 선택합니다. 리소스를 선택하면 클라우드 탐색기의 아래쪽의 두 탭, 즉 **작업** 및 **속성**에 정보가 나타납니다.

* **작업** 탭 - 선택한 리소스에 대해 클라우드 탐색기에서 수행할 수 있는 동작을 표시합니다. 또한 리소스를 클릭하여 상황에 맞는 메뉴에서 이러한 옵션을 볼 수도 있습니다.

* **속성** 탭 - 해당 유형, 로캘 및 연관된 리소스 그룹과 같은 리소스의 속성을 표시합니다.

다음 이미지에는 App Service의 각 탭에 표시되는 내용을 비교한 예제가 나와 있습니다.

  ![클라우드 탐색기 스크린샷](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

모든 리소스에는 **포털에서 열기**작업이 있습니다. 이 작업을 선택하면 클라우드 탐색기는 [Azure 포털](https://portal.azure.com)에서 선택한 리소스를 표시합니다. **포털에서 열기** 기능은 여러 층으로 중첩된 리소스를 탐색하기에 더욱 간편합니다.

추가 작업 및 속성 값은 Azure 리소스에 따라 다르게 나타날 수도 있습니다. 예를 들어 웹앱 및 논리 앱에는 **포털에서 열기** 외에 **브라우저에서 열기** 및 **디버거 연결** 작업도 있습니다. 스토리지 계정 blob, 큐 또는 테이블을 선택하면 편집기를 열려는 작업이 나타납니다. Azure 앱에는 **URL** 및 **상태** 속성이 있으며, 스토리지 리소스에는 키와 연결 문자열 속성이 있습니다.

## <a name="find-resources-in-cloud-explorer"></a>클라우드 탐색기에서 리소스 찾기

Azure 계정 구독에서 특정 이름의 리소스를 찾으려면 **클라우드 탐색기**의 **검색** 상자에 이름을 입력 합니다.

  ![클라우드 탐색기에서 리소스 찾기](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

**검색** 상자에 문자를 입력하면 해당 문자와 일치하는 리소스만 리소스 트리에 나타납니다.
