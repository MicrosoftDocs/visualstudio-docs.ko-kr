---
title: '방법: 다른 편집기에서 편집기 호스팅 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204175"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>방법: 다른 편집기에서 편집기 호스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 호스팅 창을 부모 창으로 지정 하 여 다른 편집기 내에서 한 편집기를 호스트할 수 있습니다. 이렇게 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 자식 창 프레임에서 및 매개 변수를 설정 합니다.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>편집기를 호스팅하도록 창 프레임을 설정 하려면  
  
1. 자식 창을 만들어 편집기를 호스팅된 편집기로 지정 합니다.  
  
     이 창에는 편집기 텍스트가 이동 됩니다.  
  
2. 또는 메서드를 사용 하 여 호스팅 편집기를 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 이러한 속성을 메서드에 매개 변수로 전달 하 여 호스팅된 편집기의 창 프레임 구현에서 및 속성을 설정 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> 합니다.  
  
     이러한 매개 변수를 검색 해야 하는 경우에는 메서드에 이러한 속성을 전달 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 합니다.  
  
4. 포함 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 편집기에 대해 메서드를 호출 합니다.  
  
     편집기는 포함 하는 편집기의 호스팅된 창에 표시 됩니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 Visual Studio Team Edition 설계자의 **애플리케이션 디자이너** 는 다른 편집기를 호스트 하는 편집기 창 프레임의 한 예입니다. **애플리케이션 디자이너** 는 오른쪽 창에서 다른 디자이너를 호스팅합니다. 포함 된 각 디자이너에 대 한 디자이너 패널 (또는 **속성** 페이지)이 포함 하는 창 프레임에 추가 됩니다.
