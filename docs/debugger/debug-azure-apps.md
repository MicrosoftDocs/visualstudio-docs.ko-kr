---
title: Azure 서비스 디버그 | Microsoft Docs
description: Visual Studio를 사용하여 Azure 서비스를 디버그할 수 있습니다. 이 문서의 링크를 사용하여 이 작업을 수행하는 다양한 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 09/14/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
ms.assetid: 3d434de3-ee5f-419d-9a94-ac4ac02d635b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: a77f1291621e84eb2e13075a791e9c6735447137
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857624"
---
# <a name="debug-azure-services-in-visual-studio"></a>Visual Studio에서 Azure 서비스 디버그

Visual Studio를 사용하여 다양한 시나리오에서 Azure 서비스를 디버그할 수 있습니다.

다음 위치에서 호스트되는 프로덕션 앱을 디버그하는 방법은 아래와 같습니다.

- Visual Studio Enterprise를 사용하고 Azure App Service에서 호스트: [스냅샷 디버거를 사용하여 라이브 ASP.NET 앱 디버그](../debugger/debug-live-azure-applications.md)를 참조하세요.

- Application Insights를 사용하고 Azure App Service 또는 Service Fabric을 호스트: [.NET 앱의 예외에 대한 디버그 스냅샷](/azure/application-insights/app-insights-snapshot-debugger)을 참조하세요.

- Azure 가상 머신 또는 Azure 가상 머신 확장 집합에서 호스트: [스냅샷 디버거를 사용하여 라이브 ASP.NET Azure Virtual Machines 및 Azure Virtual Machine Scale Sets 디버그](../debugger/debug-live-azure-virtual-machines.md)를 참조하세요.

- Azure Kubernetes Service에서 호스트: [스냅샷 디버거를 사용하여 라이브 ASP.NET Azure Kubernetes Services 디버그](../debugger/debug-live-azure-kubernetes.md)를 참조하세요.

원격으로 디버그하려면 다음을 참조하세요.

- IIS(Azure App Service 또는 Azure VM)에서 ASP.NET을 원격 디버그: [Azure에서 ASP.NET 원격 디버깅](remote-debugging-azure.md)을 참조하세요.

- Azure Service Fabric에서 ASP.NET을 원격 디버그: [원격 Service Fabric 애플리케이션 디버그](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 디버깅](../debugger/index.yml)
