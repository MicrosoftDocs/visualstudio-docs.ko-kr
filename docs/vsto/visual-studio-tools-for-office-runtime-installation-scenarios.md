---
title: Visual Studio Tools for Office 런타임 설치 시나리오
description: Visual Studio 2010 Tools for Office 런타임을 설치하는 방법을 알아봅니다. 이 문서에서는 세 가지 설치 시나리오에 대해 설명합니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 671d8e929ebef1085f0bf2aedad2a3280c36514c
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448339"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools for Office 런타임 설치 시나리오

  다음 세 가지 방법으로 Visual Studio 2010 Tools for Office 런타임을 설치할 수 있습니다.

- Visual Studio를 설치할 때

- Microsoft Office를 설치할 때

- Visual Studio 2010 Tools for Office 런타임 재배포 가능 파일을 설치하는 경우

  설치된 런타임 구성 요소는 컴퓨터의 구성과 설치 시나리오에 따라 달라집니다.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>각 설치 시나리오에 설치된 런타임 구성 요소

 Visual Studio 2010 Tools for Office 런타임에는 Office 솔루션 로더, .NET Framework 3.5용 Office 확장 및 이상용 Office 확장의 세 가지 구성 요소가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 있습니다. 런타임을 설치할 때 Office 솔루션 로더가 항상 설치됩니다. .NET Framework용 Office 확장의 설치는 컴퓨터의 구성과 설치 시나리오에 따라 달라집니다. 런타임을 처음 설치할 때 Office 확장명 중 하나를 설치할 수 없는 경우 런타임은 나중에 특정 요구 사항이 충족될 때 없는 Office 확장을 자동으로 설치합니다. 런타임의 이 기능을 *요청 시 설치라고 합니다.*

 다음 표에서는 각 런타임 설치 시나리오에서 기본적으로 설치되는 런타임 구성 요소를 보여 줍니다. 각 시나리오에 대한 자세한 내용은 뒷부분에 있습니다.

|런타임 설치 시나리오|Office 솔루션 로더|.NET Framework 3.5용 Office 확장|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]용 Office 확장명|[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]용 Office 확장명|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 이상과 함께|예|예, .NET Framework 3.5가 이미 설치된 경우|예|예|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 사용|예|예, .NET Framework 3.5가 이미 설치된 경우|아니요|아니요|
|Office 2010 서비스 팩 1(SP1) 이상과 함께|예|예, .NET Framework 3.5가 이미 설치된 경우|예, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]가 이미 설치된 경우|아니요|
|Office 2013 이상|예|예, .NET Framework 3.5가 이미 설치된 경우|예, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]가 이미 설치된 경우|예, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]가 이미 설치된 경우|
|재배포 가능한 런타임과 함께|예|예, .NET Framework 3.5가 이미 설치된 경우|예, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]가 이미 설치된 경우|예, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]가 이미 설치된 경우|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Visual Studio 또는 Visual Studio용 Microsoft Office 개발자 도구 함께 런타임 설치

 Visual Studio에서 Office 개발자 도구를 설치하는 경우 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 및 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]용 Office 확장이 개발 컴퓨터에 항상 설치됩니다. .NET Framework 3.5용 Office 확장은 .NET Framework 3.5가 이미 개발 컴퓨터에 있는 경우에만 설치됩니다. [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]을 설치한 후 .NET Framework 3.5를 설치하는 경우 .NET Framework 3.5를 대상으로 하는 Office 프로젝트를 처음으로 만들 때 런타임은 .NET Framework 3.5용 Office 확장을 자동으로 설치합니다.

> [!WARNING]
> [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 이상을 사용하여 .NET Framework 3.5를 대상으로 하는 Office 프로젝트를 만들 수 없습니다.

 Office 개발자 도구를 설치하는 방법에 대한 자세한 내용은 [방법: Office 솔루션을 개발하도록 컴퓨터 구성을 참조하세요.](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)

### <a name="install-the-runtime-with-office"></a>Office를 통해 런타임 설치

 Office를 설치할 때 .NET Framework 3.5용 Office 확장은 .NET Framework 3.5가 이미 컴퓨터에 있는 경우 설치됩니다. Office 다음에 .NET Framework 3.5를 설치하는 경우 Office 애플리케이션에서 .NET Framework 3.5를 대상으로 하는 솔루션을 처음으로 로드하려고 할 때 런타임은 .NET Framework 3.5용 Office 확장을 자동으로 설치합니다.

 컴퓨터에 해당 버전의 .NET Framework 이미 있는 경우 이상용 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Office 확장도 Office와 함께 설치됩니다.

 사용자에게 애플리케이션을 사용하는 데 필요한 확장이 있는지 확인하려면 최신 버전의 Visual Studio 2010 Tools for Office 런타임 재배포 가능 파일을 솔루션의 필수 구성 요소로 포함합니다. 필수 구성요소에 대한 자세한 내용은 [배포를 위한 Office 솔루션 필수 구성요약을 참조하세요.](/previous-versions/bb608617(v=vs.110))

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>런타임 재배포 가능을 사용하여 런타임 설치

 Visual Studio 2010 Tools for Office 런타임 재배포 가능 파일을 수동으로 실행하거나 Office 솔루션을 배포할 때 재배포 가능 파일을 필수 구성 요소로 포함하여 런타임을 설치할 수 있습니다.

 Visual Studio 2010 Tools for Office 런타임 재배포 가능 파일을 사용하여 런타임을 설치하면 해당 버전의 .NET Framework 이미 컴퓨터에 있는 경우 .NET Framework 3.5용 Office 확장 및 이상용 Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 확장이 설치됩니다. 런타임이 설치될 때 컴퓨터에 이러한 .NET Framework 버전 중 하나가 없는 경우 없는 .NET Framework 버전용 Office 확장이 해당 시점에 설치되지 않습니다. 나중에 없는 .NET Framework 버전을 설치하는 경우 다음번에 해당 Office 확장을 필요로 하는 솔루션이 설치되거나(런타임이 ClickOnce를 사용하여 배포된 솔루션과 함께 설치된 경우) 로드될 때(런타임이 Windows Installer를 사용하여 배포된 솔루션과 함께 설치된 경우) 런타임은 해당 Office 확장을 자동으로 설치합니다.

 ClickOnce 솔루션에 필수 구성요약을 포함하는 방법에 대한 자세한 내용은 [방법: 최종 사용자 컴퓨터에 필수 조건 설치를 참조하여 Office 솔루션을 실행합니다.](/previous-versions/bb608608(v=vs.110)) 재배포 가능 패키지에서 런타임을 수동으로 설치하는 방법에 대한 자세한 내용은 [방법: Visual Studio Tools for Office 런타임 재배포 가능 패키지 설치를 참조하세요.](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

## <a name="see-also"></a>참조

- [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools for Office 런타임의 어셈블리](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
