---
title: .NET Core 지원
description: 이 문서에서는 Mac용 Visual Studio의 .NET Core 버전 지원에 대해 설명합니다.
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: b9892a322c0264a1bdb68d672c7fe6c6e9b08d4f
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183602"
---
# <a name="net-core-support"></a>.NET Core 지원

다음 표에서는 Mac용 Visual Studio의 안정적 버전 및 미리 보기 버전에서 지원하는 .NET Core의 버전을 보여 줍니다.

| .NET Core SDK 버전 |Mac용 Visual Studio 8.1 | Mac용 Visual Studio 8.2 | Mac용 Visual Studio 8.3 | Mac용 Visual Studio 8.4 | Mac용 Visual Studio 8.5 | Mac용 Visual Studio 8.6 |
|---------|---------|---------|---------|---------|---------|---------|
|v2.1.0-v2.1.5xx | | | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v2.2.1-v2.2.1xx | | | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v3.1 | | | |✔︎|✔︎|✔︎|
|v5.0(미리 보기) | | | | | |✔︎|

> [!IMPORTANT]
> .NET Core SDK 미리 보기 버전은 지원되지 않습니다. 릴리스 버전으로 업데이트하세요. Mac용 Visual Studio 8.4를 설치하면, .NET Core v3.1 릴리스 버전이 설치됩니다.

> [!IMPORTANT]
> 이전에 Mac용 Visual Studio 8.0과 함께 .NET Core v2.2.1xx를 사용했다면 위 표에 따라 지원되는 .NET Core 버전으로 수동으로 업데이트해야 합니다. [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) 또는 [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2)을 사용하는 것이 좋습니다.

* 8\.4, 8.5 및 8.6의 경우 기본적으로 .NET Core v3.1이 설치됩니다.
* 8\.3의 경우 기본적으로 .NET Core v 3.0이 설치됩니다.
* .NET core v2.1.700(8.1의 경우에는 v2.1.700)은 설치 관리자에서 기본적으로 설치됩니다.
* 다른 버전의.NET Core를 다운로드하려면 [dotnet 페이지](https://dotnet.microsoft.com/download/dotnet-core)를 방문하십시오.
* .NET Core 3.0을 사용하는 경우, 기본적으로 C# 버전 8이 사용됩니다. .NET Core 2.x를 사용할 때는 C# 7.3이 기본값입니다. 자세한 내용은 [C# 언어 버전 관리](/dotnet/csharp/language-reference/configure-language-version)를 참조하세요.
* Mac용 Visual Studio의 미리 보기 버전 설치에 대한 자세한 내용은 [미리 보기 릴리스 설치](/visualstudio/mac/install-preview) 가이드를 참조하세요.
