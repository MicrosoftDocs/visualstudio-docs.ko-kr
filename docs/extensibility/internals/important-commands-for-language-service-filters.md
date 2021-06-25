---
title: 언어 서비스 필터에 대한 중요 명령 | Microsoft Docs
description: Visual Studio 완전한 기능을 갖춘 언어 서비스 필터를 만들 때 지원해야 하는 중요한 명령에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dd5f65248411a7ea6b892d5b4c800718456339f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899058"
---
# <a name="important-commands-for-language-service-filters"></a>언어 서비스 필터에 대한 중요 명령
모든 기능을 갖춘 언어 서비스 필터를 만들려면 다음 명령을 처리하는 것이 좋습니다. 명령 식별자의 전체 목록은 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 관리 코드에 대한 열거형 및 비관리 코드에 대한 Stdidcmd.h 헤더 파일에 정의되어 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 있습니다. Visual Studio *SDK 설치 경로*\VisualStudioIntegration\Common\Inc에서 Stdidcmd.h 파일을 찾을 수 있습니다.

## <a name="commands-to-handle"></a>처리할 명령

> [!NOTE]
> 다음 표의 모든 명령에 대해 필터링해야 하는 것은 아닙니다.

|명령|설명|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 마우스 오른쪽 단추를 클릭할 때 전송됩니다. 이 명령은 바로 가기 메뉴를 제공할 때임을 나타냅니다. 이 명령을 처리하지 않으면 텍스트 편집기에서 언어별 명령 없이 기본 바로 가기 메뉴를 제공합니다. 이 메뉴에 사용자 고유의 명령을 포함하려면 명령을 처리하고 바로 가기 메뉴를 직접 표시합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 Ctrl+J를 형식화할 때 전송됩니다. 에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 호출하여 문 완성 상자를 표시합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 문자를 형식화할 때 전송합니다. 이 명령을 모니터링하여 트리거 문자가 입력되는 시기를 확인하고 문 완성, 메서드 팁 및 텍스트 표식(예: 구문 색 지정, 중괄호 일치 및 오류 표식)을 제공합니다. 문 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 완성을 위해 에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 메서드를 호출하고 메서드 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 팁에 대해 에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 메서드를 호출합니다. 텍스트 마커를 지원하려면 이 명령을 모니터링하여 입력할 문자에 표식 업데이트가 필요한지 여부를 확인합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 Enter 키를 입력할 때 전송합니다. 에서 메서드를 호출하여 메서드 팁 창을 해제할 시기를 확인하려면 이 명령을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 모니터링합니다. 기본적으로 텍스트 보기는 이 명령을 처리합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 백스페이스 키를 형식화할 때 전송됩니다. 모니터를 사용하여 에서 메서드를 호출하여 메서드 팁 창을 해제할 시기를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 결정합니다. 기본적으로 텍스트 보기는 이 명령을 처리합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|메뉴 또는 바로 가기 키에서 전송됩니다. 에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 호출하여 팁 창을 매개 변수 정보로 업데이트합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 변수를 마우스로 가리키거나 변수에 커서를 놓고 **편집** 메뉴의 **IntelliSense에서** **빠른 정보를** 선택하면 전송됩니다. 에서 메서드를 호출하여 팁에 있는 변수의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 형식을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 반환합니다. 디버깅이 활성 상태이면 팁에 변수 값도 표시되어야 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 Ctrl+스페이스바를 형식화할 때 전송됩니다. 이 명령은 에서 메서드를 호출하도록 언어 서비스에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 지시합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 편집 메뉴의 **고급에서** **선택 영역 주석 처리** 또는 주석 처리 **제거** **메뉴에서** 전송됩니다. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 는 사용자가 선택한 텍스트를 주석으로 표시하려고 함을 나타냅니다. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 는 사용자가 선택한 텍스트의 압축을 풀려고 함을 나타냅니다. 이러한 명령은 언어 서비스에서만 구현할 수 있습니다.|

## <a name="see-also"></a>참조
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
