---
title: Azure Cloud Services의 역할 관리
description: Visual Studio에서 Azure Cloud Services의 역할을 추가 및 제거하는 방법을 알아봅니다.
author: ghogen
manager: jillfra
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 72aba423567f0b23f09e002073fdca89c99e6f4f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280839"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Visual Studio에서 Azure Cloud Services의 역할 관리
Azure 클라우드 서비스를 만든 후 새 역할을 추가하거나 기존 역할에서 제거할 수 있습니다. 또한 기존 프로젝트를 가져오고 역할로 변환할 수 있습니다. 예를 들어, ASP.NET 웹 애플리케이션을 가져오고 웹 역할로 지정할 수 있습니다.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Azure 클라우드 서비스에 역할 추가
다음 단계에서는 Visual Studio에서 Azure 클라우드 서비스 프로젝트에 웹 또는 작업자 역할을 추가하는 과정을 안내합니다.

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 확장합니다.

1. **역할** 노드를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴를 표시합니다. 상황에 맞는 메뉴에서 **추가**를 선택한 다음 현재 솔루션에서 기존 웹 역할 또는 작업자 역할을 선택하거나 웹 또는 작업자 역할 프로젝트를 만들 수 있습니다. 또한 ASP.NET 웹 애플리케이션 프로젝트와 같은 적절한 프로젝트를 선택하고 역할 프로젝트에 연결할 수 있습니다.

   ![Azure 클라우드 서비스 프로젝트에 역할을 추가하는 메뉴 옵션](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Azure 클라우드 서비스에서 역할 제거
다음 단계에서는 Visual Studio에서 Azure 클라우드 서비스 프로젝트에 웹 또는 작업자 역할을 제거하는 과정을 안내합니다.

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 확장합니다.

1. **역할** 노드를 확장합니다.

1. 제거할 노드를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **제거**를 선택합니다.

   ![Azure 클라우드 서비스에 역할을 추가하는 메뉴 옵션](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Azure 클라우드 서비스 프로젝트에 역할 다시 추가
클라우드 서비스 프로젝트에서 역할을 제거하지만 나중에 프로젝트에 역할을 추가하려면 기본 엔드포인트 및 진단 정보 등의 역할 선언과 기본 특성이 추가됩니다. `ServiceDefinition.csdef` 파일 또는 `ServiceConfiguration.cscfg` 파일에 추가되는 리소스 또는 참조는 없습니다. 이 정보를 추가하려면 이러한 파일에 수동으로 다시 추가해야 합니다.

예를 들어, 웹 서비스 역할을 제거하고 이 솔루션에 다시 이 역할을 추가하도록 나중에 결정할 수 있습니다. 이 작업을 수행하는 경우 오류가 발생합니다. 이 오류를 방지하려면 다음 XML에 표시된 `<LocalResources>` 요소를 `ServiceDefinition.csdef` 파일에 다시 추가해야 합니다. 프로젝트에 다시 추가한 웹 서비스 역할의 이름을 요소에 대 한 이름 특성의 일부로 사용 합니다 **\<LocalStorage>** . 이 예제에서 웹 서비스 역할의 이름은 **이름은 wcfservicewebrole1**입니다.

```xml
<WebRole name="WCFServiceWebRole1">
    <Sites>
      <Site name="Web">
        <Bindings>
          <Binding name="Endpoint1" endpointName="Endpoint1" />
        </Bindings>
      </Site>
    </Sites>
    <Endpoints>
      <InputEndpoint name="Endpoint1" protocol="http" port="80" />
    </Endpoints>
    <Imports>
      <Import moduleName="Diagnostics" />
    </Imports>
    <LocalResources>
      <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
    </LocalResources>
</WebRole>
```

## <a name="next-steps"></a>다음 단계
- [Visual Studio에서 Azure 클라우드 서비스에 대한 역할 구성](vs-azure-tools-configure-roles-for-cloud-service.md)
