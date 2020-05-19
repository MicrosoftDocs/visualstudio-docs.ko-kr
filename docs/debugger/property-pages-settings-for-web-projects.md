---
title: 웹 프로젝트의 속성 설정 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7daa58004b118d46a8248428e9a9d242dfccef8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730590"
---
# <a name="property-pages-settings-for-web-projects"></a>웹 프로젝트에 대한 속성 페이지 설정
[디버그 및 릴리스 구성](../debugger/how-to-set-debug-and-release-configurations.md)에서 설명한 것처럼 **속성 페이지** 대화 상자를 사용하여 웹 사이트 디버그 구성에 대한 속성 설정을 변경할 수 있습니다. 다음 표에서는 **속성 페이지** 대화 상자에서 디버거 관련 설정을 확인할 수 있는 위치에 대해 설명합니다.

### <a name="start-options-category"></a>시작 옵션 범주

| **설정** | **설명** |
| - | - |
| **시작 작업** | 애플리케이션 시작에 관련된 옵션을 그룹화하는 제목입니다. |
| **현재 페이지 사용** | 현재 페이지를 디버깅의 시작 위치로 지정합니다. |
| **특정 페이지:** | 디버깅을 시작할 웹 페이지를 지정합니다. |
| **시작 외부 프로그램:** | 디버그 대상 프로그램을 실행하는 명령을 지정합니다. |
| **명령줄 인수:** | 위에서 지정한 명령의 인수를 지정합니다. |
| **작업 디렉터리:** | 디버깅 중인 프로그램의 작업 디렉터리를 지정합니다. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]에서는 애플리케이션이 시작된 디렉터리가 작업 디렉터리입니다. 이 디렉터리는 기본적으로 \bin\debug입니다. |
| **시작 URL** | 디버깅할 웹 애플리케이션의 위치를 지정합니다. |
| **페이지를 열지 않고 외부 애플리케이션의 요청 기다리기** | 외부 애플리케이션의 요청을 기다리도록 지정합니다. 이 옵션은 Internet Explorer 또는 다른 애플리케이션을 시작하지 않습니다. 애플리케이션에서 호출될 때 디버깅이 준비합니다. |
| **서버** | 사용할 서버에 관련된 옵션을 그룹화하는 제목입니다. |
| **기본 웹 서버 사용** | 기본 웹 서버를 사용하도록 지정합니다. |
| **사용자 지정 서버 사용** | 서버로 사용할 기본 URL을 입력할 수 있습니다. |
| **디버거** | 수행할 디버깅의 형식에 관련된 옵션을 그룹화하는 제목입니다. |
| **ASP.NET 디버깅** | [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 개발 플랫폼용으로 작성된 서버 페이지를 디버깅할 수 있습니다. **시작 URL**에서 URL을 지정해야 합니다. |
| **네이티브 코드 디버깅** | 관리되는 애플리케이션에서의 비관리 네이티브 Win32 코드에 대한 호출을 디버깅할 수 있습니다. |
| **SQL Server 디버깅** | SQL Server 데이터베이스 개체를 디버깅할 수 있습니다. |
| **Silverlight 디버깅** | Silverlight 구성 요소를 디버깅할 수 있습니다. |

## <a name="see-also"></a>참조
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)