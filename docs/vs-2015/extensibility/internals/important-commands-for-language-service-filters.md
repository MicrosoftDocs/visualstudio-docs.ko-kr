---
title: 언어 서비스 필터에 대 한 중요 한 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03bb20abf32f7c320ed56f4a649a9f43453e7694
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842027"
---
# <a name="important-commands-for-language-service-filters"></a>언어 서비스 필터에 대한 중요 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

완전 한 기능을 갖춘 언어 서비스 필터를 만들려는 경우 다음 명령을 처리 하는 것이 좋습니다. 명령 식별자의 전체 목록은 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 관리 코드에 대 한 열거와 비관리 코드에 대 한 Stdidcmd 헤더 파일에 정의 되어 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 있습니다. Stdidcmd 파일은 *Visual STUDIO SDK 설치 경로*\VisualStudioIntegration\Common\Inc.에서 찾을 수 있습니다.  
  
## <a name="commands-to-handle"></a>처리할 명령  
  
> [!NOTE]
> 다음 표의 모든 명령을 필터링 하는 것은 필수가 아닙니다.  
  
|명령|Description|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 마우스 오른쪽 단추를 클릭할 때 보냅니다. 이 명령은 바로 가기 메뉴를 제공할 시간 임을 나타냅니다. 이 명령을 처리 하지 않으면 텍스트 편집기는 언어별 명령이 없는 기본 바로 가기 메뉴를 제공 합니다. 이 메뉴에 사용자 고유의 명령을 포함 하려면 명령을 처리 하 고 바로 가기 메뉴를 직접 표시 합니다.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 CTRL + J를 입력 하면 전송 됩니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>에서 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 하 여 문 완성 상자를 표시 합니다.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 문자를 입력 하면 전송 됩니다. 이 명령을 모니터링 하 여 트리거 문자를 입력 하는 시기를 확인 하 고 구문 색 지정, 중괄호 일치 및 오류 표식과 같은 문 완성, 메서드 팁 및 텍스트 마커를 제공 합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>문 완성을 위해의 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 하 고 메서드 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 팁에 대해 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> . 텍스트 표식을 지원 하려면이 명령을 모니터링 하 여 입력 하는 문자에서 표식을 업데이트 해야 하는지 여부를 확인 합니다.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 Enter 키를 입력할 때 전송 됩니다. 에서 메서드를 호출 하 여 메서드 팁 창을 해제할 시기를 결정 하려면이 명령을 모니터링 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 합니다. 기본적으로 텍스트 뷰는이 명령을 처리 합니다.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 백스페이스 키를 입력 하면 전송 됩니다. 모니터를 통해에서 메서드를 호출 하 여 메서드 팁 창을 해제할 시기를 결정할 수 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 있습니다. 기본적으로 텍스트 뷰는이 명령을 처리 합니다.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|메뉴 또는 바로 가기 키에서 전송 됩니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>에서 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 하 여 팁 창을 매개 변수 정보로 업데이트 합니다.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 변수를 마우스로 가리키거나 커서를 변수에 배치 하 고 **편집** 메뉴의 **IntelliSense** 에서 **요약 정보** 를 선택할 때 보냅니다. 에서 메서드를 호출 하 여 팁의 변수 형식을 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . 디버깅이 활성 상태인 경우 팁에도 변수 값이 표시 됩니다.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 CTRL + 스페이스바를 입력 하면 전송 됩니다. 이 명령은에서 메서드를 호출 하도록 언어 서비스에 지시 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|메뉴에서 전송 됩니다. 일반적으로 **편집** **메뉴에서** 선택 영역을 **주석** 으로 처리 하거나 주석 **처리를 제거** 합니다. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 사용자가 선택한 텍스트를 주석 처리 하려고 함을 나타냅니다. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 사용자가 선택한 텍스트의 주석 처리를 제거 하려고 함을 나타냅니다. 이러한 명령은 언어 서비스에 의해서만 구현 될 수 있습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
