---
title: 서명 VSIX 패키지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700084"
---
# <a name="signing-vsix-packages"></a>VSIX 패키지 서명
확장 어셈블리는 Visual Studio에서 실행하기 전에 서명할 필요가 없지만 이렇게 하는 것이 좋습니다.

 확장 프로그램을 보호하고 변경되지 않았는지 확인하려면 VSIX 패키지에 디지털 서명을 추가할 수 있습니다. VSIX가 서명되면 VSIX 설치 관리자에 서명되었음을 나타내는 메시지와 서명 자체에 대한 자세한 정보가 표시됩니다. VSIX의 내용이 수정되고 VSIX가 다시 서명되지 않은 경우 VSIX 설치 관리자는 서명이 유효하지 않음을 표시합니다. 설치가 중지되지는 않지만 사용자에게 경고가 표시됩니다.

> [!IMPORTANT]
> Visual Studio 2015부터 SHA256 암호화 이외의 다른 것을 사용하여 서명된 VSIX 패키지는 잘못된 서명이 있는 것으로 식별됩니다. VSIX 설치가 차단되지 는 않지만 사용자에게 경고가 표시됩니다.

## <a name="signing-a-vsix-with-vsixsigntool"></a>VSIXSignTool을 사용하여 VSIX 서명
 [VsixSignTool의](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)nuget.org [VisualStudioExtensibility에서](https://www.nuget.org/profiles/VisualStudioExtensibility) 사용할 수 있는 SHA256 암호화 서명 도구가 있습니다.

#### <a name="to-use-the-vsixsigntool"></a>VSIXSignTool을 사용하려면

1. 프로젝트에 VSIX를 추가합니다.

2. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리를 &#124; 추가를 선택합니다.**  NuGet 및 NuGet 패키지 추가에 대한 자세한 내용은 [NuGet 설명서](/NuGet) 및 [패키지 관리자 UI](/NuGet/Tools/Package-Manager-UI) 항목을 참조하십시오.

3. VisualStudioExtensibility에서 VSIXSignTool을 검색하고 NuGet 패키지를 설치합니다.

4. 이제 프로젝트의 로컬 패키지 위치에서 VSIXSignTool을 실행할 수 있습니다. 서명 시나리오(VSIXSignTool.exe /?)에 대한 도구의 명령줄 도움말을 참조하십시오.

   예를 들어 암호로 보호된 인증서 파일로 서명하려면 다음을 수행합니다.

   VSIXSignTool.exe 기호 \</f 인증 파일 \<> \</p 암호> VSIXfile>

## <a name="see-also"></a>참조
- [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
