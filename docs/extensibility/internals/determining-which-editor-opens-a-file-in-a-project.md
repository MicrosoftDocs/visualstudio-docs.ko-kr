---
title: 프로젝트에서 파일을 열 편집기를 확인 하는 중 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708650"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>프로젝트에서 파일을 여는 편집기 결정
사용자가 프로젝트에서 파일을 열면 환경에서 폴링 프로세스를 진행 한 후 해당 파일에 적절 한 편집기나 디자이너를 엽니다. 환경에서 사용 하는 초기 절차는 표준 편집기와 사용자 지정 편집기에 대해 동일 합니다. 환경에서는 파일을 여는 데 사용할 편집기를 폴링하는 경우 다양 한 기준을 사용 하 고 VSPackage는이 프로세스 중에 환경과 조정 되어야 합니다.

 예를 들어 사용자가 **파일** 메뉴에서 **열기** 명령을 선택한 다음 파일 *이름 .rtf* (또는 확장명이 *.rtf* 인 다른 파일)를 선택 하면 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 각 프로젝트에 대 한 구현을 호출 하 여 솔루션의 모든 프로젝트 인스턴스를 순환 합니다. 프로젝트는 우선 순위에 따라 문서에 대 한 클레임을 식별 하는 플래그 집합을 반환 합니다. 환경에서는 가장 높은 우선 순위를 사용 하 여 적절 한 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 합니다. 폴링 프로세스에 대 한 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)를 참조 하세요.

 기타 파일 프로젝트는 다른 프로젝트에서 요청 하지 않은 모든 파일을 클레임 합니다. 이러한 방식으로 사용자 지정 편집기는 표준 편집기에서 문서를 열기 전에 문서를 열 수 있습니다. 기타 파일 프로젝트에서 파일을 클레임 하는 경우 환경에서는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 하 여 표준 편집기를 사용 하 여 파일을 엽니다. 환경에서는 *.rtf* 파일을 처리 하는 편집기에 대해 등록 된 편집기의 내부 목록을 검사 합니다. 이 목록은 레지스트리의 다음 키에 있습니다.

 **HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ \<version> \\C\\c\\\extension \\ \<editor factory guid>**

 또한이 환경에서는 하위 키 **Docobject**가 있는 개체에 대 한 **HKEY_CLASSES_ROOT \clsid** 키의 클래스 식별자를 확인 합니다. 파일 확장명이 있는 경우 Microsoft Word와 같은 응용 프로그램의 포함 된 버전이 Visual Studio에서 바로 만들어집니다. 이러한 문서 개체는 인터페이스를 구현 하는 복합 파일 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> 이거나 개체에서 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

 레지스트리에 *.rtf* 파일에 대 한 편집기 팩터리가 없는 경우 해당 환경에서는 **HKEY_CLASSES_ROOT \\ .rtf** 키를 찾아 해당 편집기에서 지정한 편집기를 엽니다. **HKEY_CLASSES_ROOT**에서 파일 확장명을 찾을 수 없는 경우 Visual Studio core 텍스트 편집기를 사용 하 여 파일 (텍스트 파일 인 경우)을 엽니다.

 파일이 텍스트 파일이 아닌 경우에 발생 하는 핵심 텍스트 편집기에 오류가 발생 하면 해당 파일에 바이너리 편집기를 사용 합니다.

 환경에서 레지스트리에서 *.rtf* 확장명에 대 한 편집기를 찾으면이 편집기 팩터리를 구현 하는 VSPackage을 로드 합니다. 환경에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 새 VSPackage에서 메서드를 호출 합니다. VSPackage는 `QueryService` 메서드를 `SID_SVsRegistorEditor` 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 환경에 편집기 팩터리를 등록 하는를 호출 합니다.

 이제 환경에서 등록 된 편집기의 내부 목록을 재확인 하 여 *.rtf* 파일에 대해 새로 등록 된 편집기 팩터리를 찾습니다. 환경에서는 메서드의 구현을 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 만들 파일 이름 및 뷰 형식을 전달 합니다.

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
