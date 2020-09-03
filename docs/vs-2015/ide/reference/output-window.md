---
title: 출력 창 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f17b91cc462b6f628100ffbf370fcdec2eb9888d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662192"
---
# <a name="output-window"></a>출력 창
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**출력** 창에는 IDE(통합 개발 환경)의 다양한 기능에 대한 상태 메시지가 표시될 수 있습니다. **출력** 창을 열려면 메뉴 모음에서 **보기/출력**을 선택합니다(또는 CTRL + ALT + O 클릭).

> [!WARNING]
> Visual Studio Express 버전의 [보기] 메뉴에는 [출력] 창이 나타나지 않습니다. 창을 표시하려면 바로 가기 키 CTRL + ALT + O를 사용합니다.

## <a name="toolbar"></a>도구 모음
 **출력 표시** 보려는 출력 창을 하나 이상 표시 합니다. 사용자에게 메시지를 전달할 때 **출력** 창을 사용한 IDE의 도구에 따라 여러 정보 창이 제공될 수 있습니다.

 **코드에서 메시지 찾기** 코드 편집기에서 삽입 지점을 선택한 빌드 오류가 포함 된 줄로 이동 합니다.

 **이전 메시지로 이동** **출력** 창의 포커스를 이전 빌드 오류로 변경 하 고 코드 편집기에서 삽입 지점을 해당 빌드 오류가 포함 된 줄로 이동 합니다.

 **다음 메시지로 이동** **출력** 창의 포커스를 다음 빌드 오류로 변경 하 고 코드 편집기에서 삽입 지점을 해당 빌드 오류가 포함 된 줄로 이동 합니다.

 **모두 지우기** **출력** 창에서 모든 텍스트를 지웁니다.

 **자동 줄 바꿈 설정/해제** **출력** 창에서 자동 줄 바꿈 기능을 설정 및 해제 합니다. 자동 줄 바꿈이 켜지면 보기 영역을 벗어나는 더 긴 항목의 텍스트가 다음 줄에 표시됩니다.

## <a name="output-pane"></a>출력 창
 **출력 보기 선택** 목록에서 선택된 **출력** 창에는 지정된 소스의 출력이 표시됩니다.

## <a name="routing-messages-to-the-output-window"></a>출력 창으로 메시지 라우팅
 프로젝트를 빌드할 때마다 **출력** 창을 표시하려면 **일반, 프로젝트 및 솔루션, 옵션** 대화 상자에서 **빌드를 시작할 때 출력 창 표시**를 선택합니다. 그런 다음 편집용으로 열린 코드 파일을 사용하여 **출력** 창 도구 모음에서 **다음 메시지로 이동** 및 **이전 메시지로 이동** 단추를 선택하여 **출력** 창의 항목을 선택합니다. 이 작업을 수행하면 코드 편집기의 삽입 지점이 선택된 문제가 발생한 코드 줄로 이동합니다.

 [명령 창](../../ide/reference/command-window.md)에서 호출된 특정 IDE 기능 및 명령은 해당 출력을 **출력** 창으로 전달합니다. [외부 도구 관리](../../ide/managing-external-tools.md)에서 **출력 창 사용**을 선택하면 일반적으로 명령 프롬프트 창에 표시되는 .bat 및 .com 파일과 같은 외부 도구의 출력이 **출력** 창으로 라우팅됩니다. 다른 종류의 메시지는 대부분 **출력** 창에도 표시될 수 있습니다. 예를 들어 저장 프로시저의 Transact-SQL 구문이 대상 데이터베이스에 대해 확인되면 결과는 **출력** 창에 표시됩니다.

 런타임에 진단 메시지를 **출력** 창에 쓰도록 자체 애플리케이션을 프로그래밍할 수도 있습니다. 이렇게 하려면 .NET Framework 클래스 라이브러리의 <xref:System.Diagnostics> 네임스페이스에서 <xref:System.Diagnostics.Debug> 클래스 또는 <xref:System.Diagnostics.Trace> 클래스의 멤버를 사용합니다. <xref:System.Diagnostics.Debug> 클래스의 멤버는 솔루션 또는 프로젝트의 디버그 구성을 빌드할 때 출력을 표시하고, <xref:System.Diagnostics.Trace> 클래스의 멤버는 디버그 또는 릴리스 구성을 빌드할 때 출력을 표시합니다. 자세한 내용은 [출력 창에 표시되는 진단 메시지](../../debugger/diagnostic-messages-in-the-output-window.md)를 참조하세요.

 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]에서 경고 및 오류가 **출력** 창에서 표시되고 계산되는 사용자 지정 빌드 단계 및 빌드 이벤트를 만들 수 있습니다. 출력 줄에서 F1 키를 눌러 해당 도움말 항목을 표시할 수 있습니다. 자세한 내용은 [사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식 지정](https://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da)을 참조하세요.

## <a name="scrolling-behavior"></a>스크롤 동작
 [출력] 창에서 자동 스크롤을 사용하고 마우스나 화살표 키로 이동하면 자동 스크롤이 중지됩니다. 자동 스크롤을 다시 시작하려면 CTRL+END를 누릅니다.

## <a name="see-also"></a>관련 항목
 [출력 창의 진단 메시지](../../debugger/diagnostic-messages-in-the-output-window.md) [방법: 출력 창 제어](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858) [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) [빌드 구성 이해 및 빌드](../../ide/understanding-build-configurations.md) [클래스 라이브러리 개요](https://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)
