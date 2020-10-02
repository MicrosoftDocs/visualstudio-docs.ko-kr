---
title: 옵션 대화 상자, 환경, 일반
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfd1b876e58c05c668fd74087d5131bb1e9fcd40
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135094"
---
# <a name="options-dialog-box-environment--general"></a>옵션 대화 상자: 환경 \> 일반

이 페이지에서는 IDE(통합 개발 환경)에 대한 다른 옵션 중에서도 색 테마, 상태 표시줄 설정 및 파일 확장명 연결을 변경할 수 있습니다. **도구** 메뉴를 열고 **옵션**을 선택한 다음 **환경** 폴더를 열고 **일반** 페이지를 선택하여 **옵션** 대화 상자에 액세스할 수 있습니다.

## <a name="visual-experience"></a>시각적 효과

**색 테마**

IDE의 **파랑**, **밝게**, **어둡게** 또는 **파랑(추가 대비)** 색 테마를 선택합니다.

[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)에서 **Visual Studio 색 테마 편집기**를 다운로드 및 설치하여 미리 정의된 추가 테마를 설치하고 사용자 지정 테마를 만들 수 있습니다. 이 도구를 설치하면 **색 테마** 목록 상자에 다른 색 테마가 추가로 나타납니다.

**메뉴 모음에 제목 대/소문자 스타일 적용**

메뉴에서 기본적으로 제목 대/소문자 스타일을 사용합니다. 모두 대문자 스타일을 대신 사용하려면 이 옵션을 선택 취소합니다.

::: moniker range=">=vs-2019"

**픽셀 밀도가 다른 화면의 렌더링 최적화(다시 시작해야 함)**

이 옵션은 모니터별 DPI(인치당 도트 수) 인식(또는 *PMA*)을 사용하거나 사용하지 않도록 설정합니다. PMA를 사용하도록 설정하면 여러 모니터를 포함하여 모든 모니터 디스플레이 배율 및 DPI 구성에서 Visual Studio 사용자 인터페이스가 선명하게 표시됩니다. PMA를 사용하려면 Windows 10 2018년 4월 업데이트 이상 및 .NET Framework 4.8 이상이 필요합니다. 이러한 두 필수 조건이 충족되지 않으면 이 옵션은 회색으로 표시됩니다.

> [!TIP]
> - Windows 10에는 **Let Windows try to fix apps so they're not blurry**(Windows에서 앱이 흐려 보이지 않도록 수정 허용)라는 설정이 있습니다. **픽셀 밀도가 다른 화면의 렌더링 최적화** 옵션이 선택된 경우 해당 Windows 설정을 **켜면** 효과가 별로 없습니다.
> - Windows 10에는 **프로그램 호환성 문제 해결사**도 있습니다. Visual Studio의 모양을 수정하는 데는 해당 문제 해결사를 사용하지 않는 것이 좋습니다.

::: moniker-end

**클라이언트 성능에 따른 시각적 효과 자동 조정**

Visual Studio에서 시각적 효과 조정을 자동으로 설정하는지 또는 명시적으로 조정을 설정하는지를 지정합니다. 이러한 조정은 색 표시를 그라데이션에서 단색으로 변경하거나 메뉴 또는 팝업 창에서 애니메이션 사용을 제한할 수 있습니다.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10에는 **Let Windows try to fix apps so they're not blurry**(Windows에서 앱이 흐려 보이지 않도록 수정 허용)라는 설정이 있습니다. Visual Studio가 모니터에서 흐려 보이는 경우 해당 설정을 **켜는** 것이 좋습니다. [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)로 업그레이드하는 것이 좋습니다. 이 버전은 모니터별 인치당 도트 인식 애플리케이션이므로 디스플레이 선명도가 크게 향상되었습니다.

::: moniker-end

**리치 클라이언트 시각적 효과 사용**

그라데이션 및 애니메이션을 포함하여 Visual Studio의 완전한 시각적 효과를 사용하도록 설정합니다. 이러한 기능으로 인해 성능이 저하될 수 있으므로 원격 데스크톱 연결 또는 이전 그래픽 어댑터를 사용하는 경우에는 이 옵션을 선택 취소합니다. 이 옵션은 **클라이언트 성능에 따른 시각적 효과 자동 조정** 옵션을 선택 취소하는 경우에만 사용할 수 있습니다.

**사용 가능한 경우 하드웨어 그래픽 가속 기능 사용**

소프트웨어 가속 대신 하드웨어 그래픽 가속을 사용합니다(사용 가능한 경우).

## <a name="other"></a>기타

**창 메뉴에 표시할 항목**

**창** 메뉴의 Windows 목록에 표시되는 창 수를 사용자 지정합니다. 1과 24 사이의 숫자를 입력합니다. 기본값은 10입니다.

**최근 사용한 목록에 표시되는 항목**

**파일** 메뉴에 표시되는 가장 최근에 사용한 프로젝트 및 파일 수를 사용자 지정합니다. 1과 24 사이의 숫자를 입력합니다. 기본값은 10입니다. 이 방법으로 최근에 사용한 프로젝트 및 파일을 쉽게 검색할 수 있습니다.

**상태 표시줄 표시**

상태 표시줄을 표시합니다. 상태 표시줄은 IDE 창의 맨 아래에 있고 진행 중인 작업의 진행률에 대한 정보를 표시합니다.

**[닫기] 단추가 활성 도구 창에만 영향을 줌**

**닫기** 단추를 클릭할 때 도킹된 집합의 모든 도구 창이 아니라 포커스가 있는 도구 창만 닫히도록 지정합니다. 이 옵션은 기본적으로 선택됩니다.

**[자동 숨기기] 단추가 활성 도구 창에만 영향을 줌**

**자동 숨기기** 단추를 클릭할 때 도킹된 집합의 모든 도구 창이 아니라 포커스가 있는 도구 창만 자동으로 숨겨지도록 지정합니다. 기본적으로 이 옵션은 선택되어 있지 않습니다.

## <a name="see-also"></a>참고 항목

- [창 레이아웃 사용자 지정](../../ide/customizing-window-layouts-in-visual-studio.md)
