---
title: 옵션 대화 상자, 환경, 일반 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83fc6adeba0529be03a9a982713d0584a2a7bc45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661270"
---
# <a name="general-environment-options-dialog-box"></a>옵션 대화 상자, 환경, 일반
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 페이지에서는 IDE(통합 개발 환경)에 대한 다른 옵션 중에서도 색 테마, 상태 표시줄 설정 및 파일 확장명 연결을 변경할 수 있습니다. **도구** 메뉴를 열고 **옵션**을 선택한 다음 **환경** 폴더를 열고 **일반** 페이지를 선택하여 **옵션** 대화 상자에 액세스할 수 있습니다. 이 페이지가 목록에 나타나지 않으면 **옵션** 대화 상자에서 **모든 설정 표시** 확인란을 선택합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴를 열고 **설정 가져오기 및 내보내기**를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="visual-experience"></a>시각적 효과
 **색 테마** IDE의 **파란색**, **밝은** 색 또는 **짙은** 색 테마를 선택 합니다.

 [Visual Studio Marketplace](https://marketplace.visualstudio.com)에서 **Visual Studio 2015 색 테마 편집기**를 다운로드 및 설치하여 미리 정의된 추가 테마를 설치하고 사용자 지정 테마를 만들 수 있습니다. 이 도구를 설치하면 색 테마 목록 상자에 추가적인 색 테마가 나타납니다.

 메뉴 모음 메뉴에 제목 대/소문자 적용은 기본적으로 Visual Studio 2015에 **대 한 제목 대/소문자 구분** 입니다. **모두 대문자로**로 설정하려면 이 옵션의 선택을 취소하세요.

 **클라이언트 성능에 따라 시각적 효과 자동 조정** Visual Studio가 시각적 효과에 대 한 조정을 자동으로 설정 하는지 또는 명시적으로 조정을 설정할지를 지정 합니다. 이러한 조정은 색 표시를 그라데이션에서 단색으로 변경하거나 메뉴 또는 팝업 창에서 애니메이션 사용을 제한할 수 있습니다.

 **리치 클라이언트 환경 사용** 그라데이션 및 애니메이션을 포함 하 여 Visual Studio의 전체 시각적 환경을 사용 하도록 설정 합니다. 이러한 기능으로 인해 성능이 저하될 수 있으므로 원격 데스크톱 연결 또는 이전 그래픽 어댑터를 사용하는 경우에는 이 옵션을 선택 취소합니다. 이 옵션은 **클라이언트 성능에 따른 시각적 효과 자동 조정** 옵션을 선택 취소하는 경우에만 사용할 수 있습니다.

 사용 **가능한 경우 하드웨어 그래픽 가속 사용** 소프트웨어 가속 대신 하드웨어 그래픽 가속을 사용 합니다 (사용 가능한 경우).

## <a name="other"></a>기타
 **창 메뉴에 표시된 항목**은 **창** 메뉴의 Windows 목록에 표시되는 창 수를 사용자 지정합니다. 1과 24 사이의 숫자를 입력하며 기본적으로 개수는 10개입니다.

 **최근 사용된 목록에 표시된 항목**은 **파일** 메뉴에 표시되는 가장 최근에 사용한 프로젝트 및 파일 수를 사용자 지정합니다. 1과 24 사이의 숫자를 입력하며 기본적으로 개수는 10개입니다. 이 방법으로 최근에 사용한 프로젝트 및 파일을 쉽게 검색할 수 있습니다.

 **상태 표시줄 표시**는 상태 표시줄을 표시합니다. 상태 표시줄은 IDE 창의 맨 아래에 있고 진행 중인 작업의 진행률에 대한 정보를 표시합니다.

 **활성 도구 창에서만 닫기 단추 수행**은 **닫기** 단추를 클릭할 때 도킹된 집합의 모든 도구 창이 아니라 포커스가 있는 도구 창만 닫히도록 지정합니다. 이 옵션은 기본적으로 선택됩니다.

 **활성 도구 창에서만 자동 숨기기 단추 수행**은 **자동 숨기기** 단추를 클릭할 때 도킹된 집합의 모든 도구 창이 아니라 포커스가 있는 도구 창만 닫히도록 지정합니다. 기본적으로 이 옵션은 선택되어 있지 않습니다.

 **파일 연결 관리** 일반적으로 Visual Studio와 연결 된 항목의 파일 확장명과 각 파일 형식을 열기 위한 현재 기본 프로그램을 볼 수 있는 **Windows 프로그램 연결 설정** 대화 상자를 표시 합니다. 아직 연결되지 않은 파일 형식에 대한 기본 애플리케이션으로 Visual Studio를 설정하려면 파일 확장명을 선택한 다음 **저장**을 선택합니다.

 이 옵션은 두 버전의 Visual Studio가 동일한 컴퓨터에 설치되어 있고 나중에 버전 중 하나를 제거하는 경우에 유용할 수 있습니다. 제거하면 Visual Studio 파일 아이콘이 더 이상 파일 탐색기에 나타나지 않습니다. 또한 Windows에서 이러한 파일을 편집하기 위한 기본 애플리케이션으로 Visual Studio를 더 이상 인식하지 않습니다. 이 옵션은 이러한 연결을 복원합니다.

## <a name="see-also"></a>관련 항목
 [옵션 대화 상자, 환경](../../ide/reference/environment-options-dialog-box.md) [이 창 레이아웃 사용자 지정](../../ide/customizing-window-layouts-in-visual-studio.md)
