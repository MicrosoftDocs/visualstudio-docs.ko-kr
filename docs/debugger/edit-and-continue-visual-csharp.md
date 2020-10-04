---
title: 편집하며 계속하기(Visual C#) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 62411229acd2d2f8462984789037fc832dac09b8
ms.sourcegitcommit: 822e61c69514e9f564d37ba6ca6832ccf7fbc60d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91421643"
---
# <a name="edit-and-continue-visual-c"></a>편집하며 계속하기(Visual C#)
 C#에서 편집하며 계속하기를 사용하면 디버깅하는 동안 중단 모드에서 코드를 변경할 수 있습니다. 디버깅 세션을 중지하고 다시 시작하지 않고도 변경 내용을 적용할 수 있습니다. 실행 모드에서 소스 편집기는 읽기 전용입니다.

 편집하며 계속하기에서는 디버깅 세션 중에 수행할 수 있는 대부분의 변경 내용을 지원하지만 몇 가지 예외가 있습니다. 자세한 내용은 [지원되는 코드 변경(C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)을 참조하세요.

 편집하며 계속하기는 Windows 10 기반 UWP와 .NET Framework 4.6 데스크톱 이상 버전을 대상으로 하는 x86 및 x64 앱에서 지원됩니다(.NET Framework는 데스크톱 버전에만 해당함).

 > [!NOTE]
 > 지원되지 않는 앱 및 플랫폼에는 Silverlight 5 및 Windows 8.1이 있습니다.

 편집하며 계속하기가 활성화된 경우 **계속**, **설정**, **다음 명령문 설정** 등의 디버거 실행 명령을 사용하거나 디버거 창에서 함수를 실행하면 지원되는 변경 내용이 자동으로 적용됩니다.

 자세한 내용은 [방법: 편집하며 계속하기를 사용합니다(C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>참조
- [방법: 편집하며 계속하기 사용(C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [지원되는 코드 변경(C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Visual Studio에서 XAML 핫 다시 로드를 사용하여 XAML 코드 작성 및 실행 중인 XAML 코드 디버그](../xaml-tools/xaml-hot-reload.md)
