---
title: 핵심 편집기 내 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203946"
---
# <a name="inside-the-core-editor"></a>핵심 편집기 내부
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]핵심 편집기는 텍스트 정보를 수정 하 고 쿼리 하는 데 사용할 수 있는 여러 구성 요소 집합입니다. 레거시 API를 사용 하 여 핵심 편집기를 사용자 지정한 경우 편집기 어댑터를 통해 라우팅되는 이러한 사용자 지정을 계속 사용할 수 있습니다. 그러나 사용자 지정을 새 편집기 API에 맞게 조정 하는 것이 좋습니다.  
  
 다음 영역은 핵심 편집기의 몇 가지 중요 한 측면입니다.  
  
- 텍스트 버퍼  
  
- 텍스트 보기  
  
- 코드 창  
  
- 텍스트 표식  
  
- 텍스트 관리자  
  
- 언어 서비스와의 통합  
  
## <a name="in-this-section"></a>섹션 내용  
 [레거시 API를 사용하여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 를 사용 하 여 핵심 편집기의 인스턴스를 만드는 방법에 대 한 단계별 지침을 제공 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 합니다.  
  
 [레거시 API를 사용하여 텍스트 버퍼에 액세스](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 핵심 편집기에서 텍스트 버퍼의 역할에 대해 설명 하 고, 버퍼에 액세스 하는 데 사용 되는 관련 시스템에 대해 설명 하 고, 텍스트 버퍼 개체에서 구현 하는 인터페이스의 목록을 제공 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 합니다.  
  
 [레거시 API의 텍스트 버퍼 이벤트](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 텍스트 버퍼 이벤트의 알림에 사용 되는 인터페이스의 목록을 제공 합니다.  
  
 [방법: 레거시 API를 사용하여 텍스트 버퍼 이벤트에 등록](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 텍스트 버퍼 이벤트를 알리는 방법을 설명 합니다.  
  
 [텍스트 관리자를 사용하여 글로벌 설정 모니터링](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 텍스트 관리자를 사용 하 여 핵심 편집기 구성 요소와 전역 기본 설정 정보를 공유 하는 방법과 텍스트 관리자 이벤트 알림을 받는 방법을 설명 합니다.  
  
 [레거시 API를 사용하여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 핵심 편집기에서 텍스트 뷰의 역할에 대해 설명 하 고 개체에 의해 구현 된 인터페이스를 나열 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 [레거시 API를 사용하여 코드 Windows 사용자 지정](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 코드 창을 사용 하 여 텍스트 뷰를 묶는 방법에 대 한 정보를 제공 하 고 코드 창 관리자를 사용 하 여 코드 창에 장식을 제공 하는 방법에 대해 설명 하 고 새 보기에 대 한 알림을 제공 합니다.  
  
 [레거시 API를 사용하여 보기 설정 변경](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 강제로 보기 설정 및 강제 설정을 제거 하는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [언어 서비스 및 핵심 편집기](../extensibility/language-services-and-the-core-editor.md)  
 코드 장식을 제어 하기 위해 언어 서비스를 인스턴스화하는 방법을 설명 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [연습: 코어 편집기 만들기 및 편집기 파일 형식 등록](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 관리 코드에서 핵심 편집기를 시작 하는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [드롭다운 표시줄](../extensibility/drop-down-bar.md)  
 코드 창에서 드롭다운 모음을 사용 하는 방법에 대해 설명 하 고 드롭다운 막대를 구현할 때 사용 되는 인터페이스에 대해 설명 합니다.  
  
 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)  
 텍스트 표식의 개념과 핵심 편집기에서 사용 하는 방법에 대해 설명 하 고 텍스트 표식에 액세스 하 고 관리 하는 데 사용 되는 인터페이스를 나열 합니다.  
  
 [방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)  
 텍스트 표식을 만드는 방법 및 사용자 지정 명령을 바로 가기 메뉴에 추가 하는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)  
 사용자 지정 텍스트 표식을 만드는 방법 및 표식 유형을 서비스로 제공 하는 방법에 대 한 단계별 지침을 제공 합니다.
