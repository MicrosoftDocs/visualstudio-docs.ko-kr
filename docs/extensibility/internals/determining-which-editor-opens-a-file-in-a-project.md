---
title: 프로젝트에서 파일을 여는 편집기 결정 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708650"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>프로젝트에서 파일을 여는 편집기 결정
사용자가 프로젝트에서 파일을 열면 환경은 폴링 프로세스를 거치게 되어 결국 해당 파일에 대한 적절한 편집기 또는 디자이너를 엽니다. 환경에서 사용하는 초기 절차는 표준 편집기와 사용자 지정 편집기 모두에서 동일합니다. 환경은 파일을 여는 데 사용할 편집기를 폴링할 때 다양한 기준을 사용하며 VSPackage는 이 프로세스 중에 환경과 조정해야 합니다.

 예를 들어 사용자가 **파일** 메뉴에서 **열기** 명령을 선택한 다음 *filename.rtf(또는* *.rtf* 확장자가 있는 다른 파일)를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 선택하면 환경이 각 프로젝트에 대한 구현을 호출하여 결국 솔루션의 모든 프로젝트 인스턴스를 순환합니다. 프로젝트는 우선 순위에 따라 문서의 클레임을 식별하는 플래그 집합을 반환합니다. 가장 높은 우선 순위를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 환경은 적절한 메서드를 호출합니다. 폴링 프로세스에 대한 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가를](../../extensibility/internals/adding-project-and-project-item-templates.md)참조하십시오.

 기타 파일 프로젝트는 다른 프로젝트에서 주장하지 않는 모든 파일을 클레임합니다. 이렇게 하면 사용자 지정 편집자는 표준 편집기에서 문서를 열기 전에 문서를 열 수 있습니다. 기타 파일 프로젝트가 파일을 클레임하는 경우 환경은 표준 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 편집기로 파일을 여는 메서드를 호출합니다. 환경은 *.rtf* 파일을 처리하는 편집기의 내부 목록을 확인합니다. 이 목록은 다음 키의 레지스트리에 있습니다.

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<버전>\편집자\\\<편집자 공장 guid>\확장**

 또한 환경은 하위 **키 DocObject**가 있는 개체에 대해 **HKEY_CLASSES_ROOT\CLSID** 키의 클래스 식별자를 검사합니다. 파일 확장명이 발견되면 Microsoft Word와 같은 응용 프로그램의 임베디드 버전이 Visual Studio에서 만들어집니다. 이러한 문서 개체는 인터페이스를 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> 구현하는 복합 파일이거나 개체가 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 구현해야 합니다.

 레지스트리에 *.rtf* 파일에 대한 편집기 팩터기가 없는 경우 환경은 **HKEY_CLASSES_ROOT\\.rtf** 키에서 보이며 지정된 편집기가 열립니다. **HKEY_CLASSES_ROOT**파일 확장명이 없는 경우 환경은 Visual Studio 핵심 텍스트 편집기를 사용하여 텍스트 파일인 경우 파일을 엽니다.

 파일이 텍스트 파일이 아닌 경우 발생하는 핵심 텍스트 편집기에서 오류가 발생하면 환경은 파일에 이진 편집기(이진 편집기)를 사용합니다.

 환경이 레지스트리에서 *.rtf* 확장에 대한 편집을 찾으면 이 편집기 팩터리를 구현하는 VSPackage를 로드합니다. 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 새 VSPackage에서 메서드를 호출합니다. VSPackage는 `QueryService` 메서드를 `SID_SVsRegistorEditor` <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 사용하여 편집기 팩터리를 환경에 등록해야 합니다.

 이제 환경은 *.rtf* 파일에 대해 새로 등록된 편집기 팩터리를 찾기 위해 등록된 편집기의 내부 목록을 다시 확인합니다. 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 만들 파일 이름 및 보기 형식을 전달하여 메서드의 구현을 호출합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
