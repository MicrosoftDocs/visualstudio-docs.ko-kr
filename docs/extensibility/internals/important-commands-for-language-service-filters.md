---
title: 언어 서비스 필터에 대한 중요 명령 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707619"
---
# <a name="important-commands-for-language-service-filters"></a>언어 서비스 필터에 대한 중요 명령
완전한 기능을 갖춘 언어 서비스 필터를 만들려면 다음 명령을 처리하는 것이 좋습니다. 명령 식별자의 전체 목록은 관리되는 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 코드의 열거형과 관리되지 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 않는 코드의 Stdidcmd.h 헤더 파일에 정의되어 있습니다. *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Common\Inc.에서 Stdidcmd.h 파일을 찾을 수 있습니다.

## <a name="commands-to-handle"></a>처리할 명령

> [!NOTE]
> 다음 표의 모든 명령을 필터링하는 것은 필수는 아닙니다.

|명령|설명|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 마우스 오른쪽 단추로 클릭할 때 전송됩니다. 이 명령은 바로 가기 메뉴를 제공할 때임을 나타냅니다. 이 명령을 처리하지 않으면 텍스트 편집기는 언어별 명령 없이 기본 바로 가기 메뉴를 제공합니다. 이 메뉴에 사용자 고유의 명령을 포함하려면 명령을 처리하고 바로 가기 메뉴를 직접 표시합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 CTRL+J를 입력할 때 전송됩니다. 명령문 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 완료 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 상자를 표시하려면 메서드를 호출합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 문자를 입력할 때 전송됩니다. 이 명령을 모니터링하여 트리거 문자가 입력되는 시기를 확인하고 구문 색칠, 중괄호 일치 및 오류 마커와 같은 명령문 완성, 메서드 팁 및 텍스트 마커를 제공합니다. for <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 문 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 완료에 대한 메서드와 for 메서드 팁의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 호출합니다. 텍스트 마커를 지원하려면 이 명령을 모니터링하여 입력중인 문자가 마커를 업데이트해야 하는지 여부를 확인합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 Enter 키를 입력할 때 전송됩니다. 이 명령을 모니터링하여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>에서 메서드를 호출하여 메서드 팁 창을 해제할 시기를 결정합니다. 기본적으로 텍스트 보기는 이 명령을 처리합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 백스페이스 키를 입력할 때 전송됩니다. 에서 메서드를 호출하여 메서드 팁 창을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 해제할 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>시기를 결정하려면 모니터링합니다. 기본적으로 텍스트 보기는 이 명령을 처리합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|메뉴 또는 바로 가기 키에서 전송됩니다. 매개 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 변수 정보로 팁 창을 업데이트하려면 의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 메서드를 호출합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 변수 위로 마우스를 가져가거나 변수에 커서를 배치하고 **편집** 메뉴에서 **IntelliSense에서** **빠른 정보를** 선택할 때 전송됩니다. 에서 메서드를 호출 하여 팁에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 변수의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>형식을 반환합니다. 디버깅이 활성 상태인 경우 팁에 변수 값도 표시되어야 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 CTRL+SPACEBAR를 입력할 때 전송됩니다. 이 명령은 언어 서비스에 메서드를 호출하도록 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 지시합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|메뉴에서 전송되는 일반적으로 편집 **메뉴의** **고급** 에서 **주석 선택** 또는 주석 **선택 취소.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>사용자가 선택한 텍스트에 주석을 달고 있음을 나타냅니다. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 은 사용자가 선택한 텍스트의 주석을 해제하려고 음을 나타냅니다. 이러한 명령은 언어 서비스에서만 구현할 수 있습니다.|

## <a name="see-also"></a>참조
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
