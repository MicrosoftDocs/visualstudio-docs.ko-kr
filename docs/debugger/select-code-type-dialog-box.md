---
title: 코드 형식 선택 대화 상자 | Microsoft Docs
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ccfe636cd8981c2f9dcc1375fb795d6c026b572
ms.sourcegitcommit: 5e82a428795749c594f71300ab03a935dc1d523b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86211577"
---
# <a name="select-code-type-dialog-box"></a>코드 형식 선택 대화 상자

이 대화 상자를 열려면 **프로세스에 연결** 대화 상자를 열고 **선택** 단추를 클릭합니다.

**디버그할 코드 형식을 자동으로 결정** - 실행되고 있는 코드의 종류에 따라 적절한 디버거가 선택됩니다.

**다음 코드 형식 디버깅:** 제공된 목록에서 디버깅할 코드 형식을 선택합니다. 이는 [연결 실패 문제를 해결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors)하는 경우에 유용할 수 있습니다. 이 옵션은 디버그하려는 코드 형식만 검색하도록 제한합니다.

   ::: moniker range=">=vs-2019"
   - Blazor WebAssembly - 클라이언트 쪽 Blazor WebAssembly
   - GPU - 소프트웨어 에뮬레이터 - GPU 소프트웨어 에뮬레이터에서 실행되는 C++ 코드
   - JavaScript(Chrome) - Chrome에서 실행되는 JavaScript
   - JavaScript(Microsoft Edge - Chromium) - Windows 10용 Chromium 기반 Microsoft Edge에서 실행되는 JavaScript
   - JavaScript CDP(V3) 디버거 - Chrome DevTools Protocol 버전 3(CDP 클라이언트에서 디버깅에 사용됨)
   - 관리(CoreCLR) - .NET Core
   - 관리(네이티브 컴파일) - C++/CLR 코드
   - 관리(v3.5, v3.0, v2.0) - .NET Framework 2.0 이상(최대 3.5)용 .NET Framework 코드
   - 관리(v.4.6, v4.5, v4.0) - .NET Framework 4.0 이상용 .NET Framework 코드
   - 네이티브 - C/C++
   - Node.js 디버깅 - Node.js 런타임에 호스트되는 코드
   - Python - Python 
   - 스크립트 - JavaScript에 대한 일반 스크립트 디버거를 지정합니다. JavaScript(Chrome)와 같은 시나리오에 적용되는 경우 더 제한적인 옵션을 사용합니다.
   - T-SQL - Transact-SQL
   - Unity - Unity
   - 관리되는 호환성 모드 - 일반적으로 C++/CLR 코드를 사용하는 혼합 모드 디버깅에서 사용하기 위해(혼합 모드에서 편집하며 계속하기를 사용) 또는 레거시 디버거를 대상으로 하는 확장을 지원하기 위해 관리 코드에 대한 레거시 디버거를 지정합니다. 대부분의 혼합 모드 디버깅 시나리오에서는 관리되는 호환성 모드 대신 **네이티브**와 적절한 **관리** 코드 형식을 선택합니다.
   ::: moniker-end

   대부분의 시나리오에서는 동일한 디버깅 세션에서 여러 디버거를 연결하는 것은 지원되지 않습니다. Visual Studio의 두 번째 인스턴스를 사용하여 이 작업을 수행할 수 있습니다.

## <a name="see-also"></a>참조
- [디버거 보안](../debugger/debugger-security.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
