---
title: 편집하며 계속하기 오류 메시지 대화 상자 | Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df95eae689f7c3abbb0d75a7557ce749bdceee5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188226"
---
# <a name="edit-and-continue-error-message"></a>편집하며 계속하기 오류 메시지

**편집하며 계속하기** 오류 메시지 상자는 편집하며 계속하기를 지원하는 코드 언어에서 디버그할 때 표시되지만 편집하며 계속하기는 수행한 코드 변경 내용에 사용할 수 없습니다. 오류 메시지에 자세한 설명이 나와 있습니다. 대화 상자에 응답하려면 **확인**을 선택하여 대화 상자를 닫고 편집 시도를 취소합니다.

이 오류 메시지의 가능한 원인은 다음과 같습니다.

- SQL Server 코드를 편집하려고 했습니다.
- 최적화된 코드를 편집하려고 했습니다. 릴리스 빌드에서 디버그 빌드로 전환해야 할 수도 있습니다.
- 디버거에서 일시 중지된 상태가 아니라 실행 중인 코드를 편집하려고 했습니다. [중단점을 설정](../debugger/using-breakpoints.md)하고 일시 중지된 상태에서 코드를 편집해 보세요.
- 관리되지 않는 디버깅만 사용하도록 설정된 상태에서 관리 코드를 편집하려고 했습니다. 편집하며 계속하기는 [혼합 모드 디버깅](../debugger/how-to-debug-in-mixed-mode.md)에서 작동하지 않습니다.
- 프로그래밍 언어에서 편집하며 계속하기가 지원하지 않는 코드 변경을 수행하려 했습니다. 자세한 내용은 [C#에서 지원되는 코드 변경](supported-code-changes-csharp.md), [Visual Basic 편집하며 계속하기에서 지원되지 않는 편집](supported-code-changes-csharp.md) 및 [지원되는 C++ 코드 변경](supported-code-changes-cpp.md)에 대한 문서를 참조하세요.
- **디버그** 메뉴에서 디버깅을 시작하는 대신 연결된 앱에서 코드를 편집하려고 했습니다.
- Dr. Watson 덤프를 디버그하는 동안 코드를 편집하려고 했습니다. 디버깅
- **처리되지 않은 예외에 대한 호출 스택 해제** 옵션이 선택되지 않은 상태에서 처리되지 않은 예외가 발생한 후 코드를 편집하려고 했습니다.
- 포함된 런타임 애플리케이션을 디버그하는 동안 코드를 편집하려고 했습니다.
- 64비트 앱 대상으로 4.5.1보다 이전 버전의 .NET Framework를 사용하여 관리 코드를 편집하려고 했습니다. 4\.5.1 이전 버전의 .NET Framework에 편집하며 계속하기를 사용하려면 **\<ProjectName>**  > **속성** > **컴파일** 탭, **고급 컴파일러** 설정에서 대상을 **x86**으로 설정합니다.
- 디버그하는 동안 수정하여 다시 로드한 어셈블리의 코드를 편집하려고 했습니다.
- 로드되지 않은 어셈블리의 코드를 편집하려고 했습니다.
- 최신 버전에 빌드 오류가 있기 때문에 이전 버전의 앱 디버깅을 시작했습니다.

자세한 내용은 다음을 참조하세요.
- [C++ 편집하며 계속하기 블로그 게시물](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [지원되는 코드 변경(C++)](../debugger/supported-code-changes-cpp.md)
- [편집하며 계속하기](../debugger/edit-and-continue.md)