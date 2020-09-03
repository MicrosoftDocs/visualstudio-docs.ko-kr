---
title: 어셈블리 및 매니페스트 서명 관리
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a17ce633515979ca7a3fd3ac5a7e1d8802996944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770414"
---
# <a name="manage-assembly-and-manifest-signing"></a>어셈블리 및 매니페스트 서명 관리

강력한 이름 서명은 소프트웨어 구성 요소에 전역적으로 고유한 ID를 제공합니다. 강력한 이름은 어셈블리가 다른 사용자에 의해 스푸핑되지 않도록 보장하고 구성 요소 종속성 및 구성 문이 올바른 구성 요소 및 구성 요소 버전에 매핑되도록 하는 데 사용됩니다.

강력한 이름은 어셈블리 ID(단순 텍스트 이름, 버전 번호 및 문화권 정보) 및 공개 키 토큰과 디지털 서명으로 구성됩니다.

Visual Basic 및 C# 프로젝트의 어셈블리 서명에 대한 자세한 내용은 [강력한 이름의 어셈블리 만들기 및 사용](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)을 참조하세요.

C++ 프로젝트의 어셈블리 서명에 대한 자세한 내용은 [강력한 이름 어셈블리(C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)를 참조하세요.

> [!NOTE]
> 강력한 이름 서명은 어셈블리의 리버스 엔지니어링으로부터 보호하지 않습니다. 리버스 엔지니어링으로부터 보호하려면 [Dotfuscator Community](dotfuscator/index.md)를 참조하세요.

## <a name="asset-types-and-signing"></a>자산 형식 및 서명

.NET 어셈블리 및 애플리케이션 매니페스트에 서명할 수 있습니다.

- 실행 파일( *.exe*)

- 애플리케이션 매니페스트( *.exe.manifest*)

- 배포 매니페스트( *.application*)

- 공유 구성 요소 어셈블리( *.dll*)

다음 자산 형식에 서명합니다.

1. GAC(전역 어셈블리 캐시)에 배포하려는 경우 어셈블리입니다.

2. ClickOnce 애플리케이션 및 배포 매니페스트입니다. Visual Studio에서는 이러한 애플리케이션에 기본적으로 서명할 수 있습니다.

3. 주 interop 어셈블리(COM 상호 운용성에 사용됨). TLBIMP 유틸리티는 COM 형식 라이브러리에서 주 interop 어셈블리를 만들 때 강력한 이름 지정을 적용합니다.

일반적으로 실행 파일에는 서명하면 안 됩니다. 강력한 이름의 구성 요소는 애플리케이션과 함께 배포되는 강력한 이름이 아닌 구성 요소를 참조할 수 없습니다. Visual Studio에서는 애플리케이션 실행 파일에 서명하지 않고 약한 이름의 실행 파일을 가리키는 애플리케이션 매니페스트에 서명합니다. 애플리케이션 전용의 구성 요소에는 서명하지 마세요. 서명으로 인해 종속성 관리가 더 어려워질 수 있기 때문입니다.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Visual Studio에서 어셈블리에 서명하는 방법

프로젝트 속성 창의 **서명** 탭을 사용하여 애플리케이션 또는 구성 요소에 서명합니다(**솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성** 선택). **서명** 탭을 선택하고 나서 **어셈블리 서명** 확인란을 선택합니다.

키 파일을 지정합니다. 새 키 파일을 만들도록 선택하면 새 키 파일은 항상 *.pfx* 형식으로 만들어집니다. 새 파일의 이름 및 암호가 필요합니다.

> [!WARNING]
> 다른 사용자가 사용하지 못하도록 키 파일을 항상 암호로 보호해야 합니다. 공급자 또는 인증서 저장소를 사용하여 키를 보호할 수도 있습니다.

이미 만든 키를 가리킬 수도 있습니다. 키 만들기에 대한 자세한 내용은 [퍼블릭/프라이빗 키 쌍 만들기](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)를 참조하세요.

공개 키에만 액세스할 수 있는 경우 서명 연기를 사용하여 키 할당을 지연시킬 수 있습니다. **서명만 연기** 확인란을 선택하여 서명 연기를 사용하도록 설정합니다. 지연 서명된 프로젝트가 실행되지 않고 이 프로젝트를 디버그할 수 없습니다. 그러나 [Sn.exe 강력한 이름 도구](/dotnet/framework/tools/sn-exe-strong-name-tool)를 `-Vr` 옵션과 함께 사용하여 개발 중에 확인을 건너뛸 수 있습니다.

매니페스트 서명에 대한 자세한 내용은 [방법: 애플리케이션 및 배포 매니페스트 서명](../ide/how-to-sign-application-and-deployment-manifests.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [강력한 이름의 어셈블리](/dotnet/framework/app-domains/strong-named-assemblies)
- [강력한 이름의 어셈블리(C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
