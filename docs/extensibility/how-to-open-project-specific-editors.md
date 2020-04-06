---
title: '방법: 프로젝트별 편집자 열기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710834"
---
# <a name="how-to-open-project-specific-editors"></a>방법: 프로젝트별 편집기 열기
프로젝트에서 열리는 항목 파일이 해당 프로젝트의 특정 편집기에 본질적으로 바인딩된 경우 프로젝트는 프로젝트별 편집기를 사용하여 파일을 열어야 합니다. 편집기를 선택하기 위한 IDE 메커니즘에 파일을 위임할 수 없습니다. 예를 들어 표준 비트맵 편집기를 사용하는 대신 이 프로젝트별 편집기 옵션을 사용하여 프로젝트에 고유한 파일의 정보를 인식하는 특정 비트맵 편집기를 지정할 수 있습니다.

 IDE는 특정 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 프로젝트에서 파일을 열어야 한다고 결정할 때 메서드를 호출합니다. 자세한 내용은 [파일 열기 명령을 사용하여 파일 표시](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)를 참조하십시오. 다음 지침을 사용하여 프로젝트별 편집기를 사용하여 프로젝트가 파일을 열도록 하는 `OpenItem` 메서드를 구현합니다.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>프로젝트별 편집기를 사용하여 OpenItem 메서드를 구현하려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 메서드 ()`RDT_EditLock`를 호출하여 파일(문서 데이터 개체)이 이미 열려 있는지 확인합니다.

    > [!NOTE]
    > 문서 데이터 및 문서 뷰 개체에 대한 자세한 내용은 [사용자 지정 편집기의 문서 데이터 및 문서 보기를](../extensibility/document-data-and-document-view-in-custom-editors.md)참조하십시오.

2. 파일이 이미 열려 있는 경우 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 호출하고 `grfIDO` 매개 변수에 대한 IDO_ActivateIfOpen 값을 지정하여 파일을 다시 표시합니다.

     파일이 열려 있고 문서가 호출 프로젝트 이외의 프로젝트에서 소유하는 경우 열려 있는 편집기는 다른 프로젝트에서 온 것이라는 경고가 사용자에게 표시됩니다. 그런 다음 파일 창이 표시됩니다.

3. 텍스트 버퍼(문서 데이터 개체)가 이미 열려 있고 다른 뷰를 첨부하려는 경우 해당 뷰를 연결해야 합니다. 프로젝트에서 뷰(문서 보기 개체)를 인스턴스화하는 데 권장되는 방법은 다음과 같습니다.

    1. 인터페이스에 <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> 대한 포인터를 얻으려면 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> 서비스를 호출합니다. `QueryService`

    2. 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 호출하여 문서 보기 클래스의 인스턴스를 만듭니다.

4. 문서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 뷰 개체를 지정하여 메서드를 호출합니다.

     이 메서드는 문서 창에서 문서 보기 개체를 사이트합니다.

5. <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> 또는 메서드에 대한 적절한 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 호출을 수행합니다.

     이 시점에서 뷰를 완전히 초기화하고 열 준비가 되어 있어야 합니다.

6. 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 호출하여 뷰를 표시하고 엽니다.

## <a name="see-also"></a>참조
- [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)
- [방법: 열린 문서에 대한 편집기 열기](../extensibility/how-to-open-editors-for-open-documents.md)
