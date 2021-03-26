---
title: VSIX 패키지 서명 | Microsoft Docs
description: 확장 어셈블리에 서명 하는 방법에 대해 알아봅니다. Vsix 설치 관리자가 VSIX에 서명 되었다는 메시지와 서명 자체에 대 한 정보를 표시 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2a2c9703eb41c1a3e5baa023d8240b56ccbb13b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056365"
---
# <a name="signing-vsix-packages"></a>VSIX 패키지 서명
확장 어셈블리는 Visual Studio에서 실행할 수 있을 때까지 서명할 필요가 없지만 그렇게 하는 것이 좋습니다.

 확장을 보호 하 고 변조 되지 않았는지 확인 하려면 VSIX 패키지에 디지털 서명을 추가할 수 있습니다. VSIX가 서명 되 면 VSIX 설치 관리자에 서명 된 것을 나타내는 메시지와 서명 자체에 대 한 추가 정보가 표시 됩니다. Vsix의 내용이 수정 되었고 VSIX가 다시 서명 되지 않은 경우 VSIX 설치 관리자는 서명이 유효 하지 않은 것으로 표시 됩니다. 설치는 중지 되지 않지만 사용자에 게 경고를 표시 합니다.

> [!IMPORTANT]
> Visual Studio 2015부터 SHA256 암호화 이외의 항목을 사용 하 여 서명 된 VSIX 패키지는 잘못 된 서명이 있는 것으로 식별 됩니다. VSIX 설치가 차단 되지 않지만 사용자에 게 경고가 표시 됩니다.

## <a name="signing-a-vsix-with-vsixsigntool"></a>VSIXSignTool을 사용 하 여 VSIX 서명
 Nuget.org에서 [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)의 [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) 에서 사용할 수 있는 SHA256 암호화 서명 도구가 있습니다.

#### <a name="to-use-the-vsixsigntool"></a>VSIXSignTool를 사용 하려면

1. VSIX를 프로젝트에 추가 합니다.

2. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가 &#124; NuGet 패키지 관리** 를 선택 합니다.  Nuget 및 nuget 패키지를 추가 하는 방법에 대 한 자세한 내용은 [nuget 설명서](/NuGet) 및 [패키지 관리자 UI](/NuGet/Tools/Package-Manager-UI) 항목을 참조 하세요.

3. VisualStudioExtensibility에서 VSIXSignTool을 검색 하 고 NuGet 패키지를 설치 합니다.

4. 이제 프로젝트의 로컬 패키지 위치에서 VSIXSignTool을 실행할 수 있습니다. 서명 시나리오 (VSIXSignTool.exe/?)는 도구의 명령줄 도움말을 참조 하세요.

   예를 들어 암호로 보호 된 인증서 파일을 사용 하 여 서명 합니다.

   VSIXSignTool.exe 서명/f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>참조
- [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
