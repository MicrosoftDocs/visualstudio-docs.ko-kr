---
title: C#, F# 및 VB 프로젝트 디버그 준비 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Basic]
- debug builds, project settings
- Visual C# projects, debugging
- Visual Basic projects, debugging
- debugging [C#]
- debugger, settings by project type
ms.assetid: 7a0535f6-1cd4-4b51-ad34-f4a45b9f1ce3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 90e108ddd64a9b520c8ae1d0c86e416dea64e5be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738128"
---
# <a name="debugging-preparation-c-f-and-visual-basic-project-types"></a>디버깅 준비 중: C#, F# 및 Visual Basic 프로젝트 형식
이 단원의 항목에서는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 프로젝트 템플릿으로 만든 C#, F# 및 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트 형식을 디버깅하는 방법에 대해 설명합니다.

 빌드 결과로 DLL을 생성하는 프로젝트 형식은 공통적인 특징을 갖고 있기 때문에 모두 [DLL 프로젝트 디버그](../debugger/debugging-dll-projects.md)로 그룹화되었습니다.

## <a name="in-this-section"></a>섹션 내용
 [권장되는 속성 설정](../debugger/managed-debugging-recommended-property-settings.md) - 이 섹션에서는 C#, F# 및 Visual Basic 프로젝트에 권장되는 디버깅 관련 속성 설정에 관해 설명합니다.

 [Windows Forms 애플리케이션](../debugger/debugging-preparation-windows-forms-applications.md) - Windows 애플리케이션 프로젝트에 관해 설명하고 디버깅, 기본 디버그 구성 변경, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 외부에서 애플리케이션을 시작한 후에 애플리케이션에 연결 등에 관한 지침을 제공합니다.

 [콘솔 프로젝트](../debugger/debugging-preparation-console-projects.md) - C# 또는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 콘솔 애플리케이션 디버그에 관한 추가 고려 사항을 제공합니다. 이러한 정보로는 명령줄 인수 지정, 명령 프롬프트에서 애플리케이션 시작, 출력 창에 쓰기, 콘솔 창 문제 해결 등이 있습니다.

 [Windows 서비스](../debugger/debugging-preparation-windows-services.md) - Windows 서비스에 관해 설명하고 Windows 서비스 애플리케이션 디버깅으로 연결되는 링크를 제공합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md) - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 디버거를 사용하여 프로그램을 디버그하기 위해 필요한 설정 및 준비 방법을 다룹니다.

 [관리 코드 디버그](../debugger/debugging-managed-code.md) - 관리 코드로 작성된 애플리케이션에 관련된 일반적인 디버깅 문제와 디버깅 방법에 관해 설명합니다.

## <a name="see-also"></a>참조
- [디버거 보안](../debugger/debugger-security.md)