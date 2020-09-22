---
title: 연결 프로그램 명령을 사용 하 여 파일 표시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841503"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>연결 프로그램 명령을 사용하여 파일 표시
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트는 [ **연결 프로그램** ] 대화 상자를 표시 하도록 IDE에 요청할 수 있습니다. 이 요청은 표준 편집기가 선택 된 파일을 열도록 요청 하는 메시지를 표시 합니다. 다음 단계에서는 이 프로세스에 대해 설명합니다.  
  
1. 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 매개 변수에 OSE_UseOpenWithDialog 값을 지정 하 여를 호출 합니다 `OSEOpenDocEditor` .  
  
2. 문서의 파일 이름 확장명에 따라 IDE는 지정 된 문서를 열 수 있는 레지스트리에 나열 된 편집기를 확인 하 고 **연결 프로그램** 대화 상자에이 정보를 표시 합니다.  
  
    > [!NOTE]
    > **연결** 프로그램 대화 상자에 포함 해야 하는 내장 편집기가 있는 프로젝트는 이러한 각 편집기에 대 한 편집기 팩터리를 등록 해야 합니다. 내장 편집기는 메서드 구현에서 적용 되는 특정 형식의 프로젝트와 함께 작동 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 합니다. IDE에는 핵심 텍스트 편집기와 바이너리 편집기에 대 한 기본 제공 편집기 팩터리가 있습니다. 또한 IDE는 등록 된 각 Windows 파일 연결을 대신 하 여 편집기 팩터리의 인스턴스를 만듭니다. 이러한 파일의 예는 Microsoft Word입니다.  
  
3. 사용자가 **연결** 프로그램 대화 상자에서 항목을 선택 하는 즉시 IDE에서 메서드를 호출 하 여 문서를 엽니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> . 자세한 내용은 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)   
 [파일 열기 명령을 사용 하 여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)
