---
title: 동기화된 설정
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6459b6f65fd1e29fbadb01f6aa2fc51520b726b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646820"
---
# <a name="synchronized-settings-in-visual-studio"></a>Visual Studio의 동기화된 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동일한 개인 설정 계정을 사용하여 여러 컴퓨터에서 Visual Studio에 로그인하는 경우 기본적으로 설정이 모든 컴퓨터에서 동기화됩니다.

## <a name="synchronized-settings"></a>동기화된 설정
 기본적으로 다음 설정이 동기화됩니다.

- 개발 설정. Visual Studio를 처음 실행할 때 설정 집합을 선택해야 하지만 언제든지 선택을 변경할 수 있습니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.

- **도구 &#124; 옵션** 페이지의 다음 설정:

  - **환경**, **일반** 옵션 페이지의 **테마** 및 메뉴 모음 대/소문자 설정

  - **환경**, **글꼴 및 색** 옵션 페이지의 모든 설정

  - **환경**, **키보드** 옵션 페이지의 모든 바로 가기 키

  - **환경, 탭 및 창** 옵션 페이지의 모든 설정

  - **환경**, **시작** 옵션 페이지의 모든 설정

  - **텍스트 편집기** 옵션 페이지의 모든 설정

- XAML 디자이너의 옵션 페이지의 모든 설정

- 사용자 정의 명령 별칭. 명령 별칭을 정의 하는 방법에 대 한 자세한 내용은 [Visual Studio 명령 별칭](../ide/reference/visual-studio-command-aliases.md)을 참조 하세요.

- **창 &#124; 창 레이아웃 관리** 페이지의 사용자 정의 창 레이아웃

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>특정 컴퓨터에 대해 동기화된 설정 끄기
 Visual Studio의 동기화된 설정이 기본적으로 켜져 있습니다. **도구 &#124; 옵션 &#124; 환경 &#124; 동기화된 설정** 페이지로 이동하고 확인란의 선택을 취소하면 컴퓨터에서 동기화된 설정을 끌 수 있습니다.  예를 들어 컴퓨터 A에서 Visual Studio의 설정을 동기화하지 않기로 결정하면 컴퓨터 A에서 수행한 변경 사항이 컴퓨터 B나 컴퓨터 C에 나타나지 않습니다. 컴퓨터 B와 C는 계속 서로 동기화되지만 컴퓨터 A와는 동기화되지 않습니다.

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio 제품군 제품 및 버전 간에 설정 동기화
 Express 및 Community 버전을 포함하여 Visual Studio 2015 버전 간에 설정을 동기화할 수 있습니다. Blend 같은 Visual Studio 제품군 제품 간에서도 설정이 동기화됩니다. 그러나 각각의 이러한 제품군 제품에는 Visual Studio와 공유되지않는 자체 설정이 있을 수 있습니다. 예를 들어 컴퓨터 A의 Blend에 관련된 설정이 컴퓨터 B의 Blend와 공유되지만 컴퓨터 A나 B의 Visual Studio와는 공유되지 않습니다.

> [!WARNING]
> Visual Studio 2013과 Visual Studio 2015 간에 설정이 동기화되지 않습니다. Visual Studio 2015를 처음 열 때 Visual Studio 2013의 설정이 마이그레이션되지만 그 후 Visual Studio 2013으로 다시 마이그레이션할 수 없습니다.

## <a name="see-also"></a>관련 항목
 [IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)
