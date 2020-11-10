---
title: .NET Framework 확장명 등록 | Microsoft Docs
description: .NET Framework의 특정 버전을 확장하는 어셈블리를 포함하는 폴더를 시스템 레지스트리에 추가하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d63dda9cab50474fd357043d5f694a645a18b2b9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048755"
---
# <a name="register-extensions-of-the-net-framework"></a>.NET Framework 확장명 등록

.NET Framework의 특정 버전을 확장하는 어셈블리를 개발할 수 있습니다. 해당 어셈블리가 Visual Studio의 **참조 추가** 대화 상자에 표시되도록 설정하려면 이 어셈블리를 포함하는 폴더를 시스템 레지스트리에 추가해야 합니다.

 Trey Research라는 회사가 .NET Framework 4를 확장하는 라이브러리를 개발하여 프로젝트가 .NET Framework 4를 대상으로 할 때 라이브러리 어셈블리가 **참조 추가** 대화 상자에 표시되도록 하려는 경우를 예로 들어 보겠습니다. 이때 어셈블리는 32비트 컴퓨터에서 실행되는 32비트 어셈블리 또는 64비트 컴퓨터에서 실행되는 64비트 어셈블리이며 *C:\TreyResearch\Extensions4\\* 폴더에 설치된다고 가정합니다.

 다음 키를 사용하여 이 폴더를 등록합니다. **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\** 키에 다음 기본값을 제공합니다. **C:\TreyResearch\Extensions4**

> [!NOTE]
> .NET Framework 버전의 빌드 번호는 다를 수 있습니다.

 64비트 컴퓨터에서 32비트 어셈블리를 등록하려면 다음과 같이 Wow6432 노드를 사용합니다. **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**

### <a name="see-also"></a>참고 항목

- [Visual Studio 통합](../msbuild/visual-studio-integration-msbuild.md)
