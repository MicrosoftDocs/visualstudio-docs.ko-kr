---
title: Windows 서비스 디버그 준비 | Microsoft Docs
description: Windows에서 백그라운드로 실행되는 프로그램인 Windows 서비스의 디버그를 Visual Studio에서 준비합니다.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdf82b708440cb3201c5d05bd936c7f7d9c30729
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872394"
---
# <a name="debugging-preparation-windows-services"></a>디버깅 준비 중: Windows 서비스
Windows 서비스는 Microsoft Windows에서 백그라운드로 실행되는 프로그램입니다. 예를 들어, 컴퓨터의 시간을 업데이트하는 Windows 시간 서비스와 텔넷 서비스가 Windows 서비스에 포함됩니다. Windows 서비스는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 내에서 실행할 수 없고 서비스 제어 관리자의 컨텍스트 내에서 실행해야 합니다. 자세한 내용은 [Windows 서비스 만들기](/dotnet/framework/windows-services/how-to-create-windows-services), [Windows 서비스 애플리케이션 디버깅](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) 및 [Windows 서비스 애플리케이션](/dotnet/framework/windows-services/index)을 참조하세요.

## <a name="see-also"></a>참조
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [C#, F#, and Visual Basic Project Types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)(C#, F# 및 Visual Basic 프로젝트 형식)
- [C# 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [방법: OnStart 메서드 디버그](../debugger/how-to-debug-the-onstart-method.md)