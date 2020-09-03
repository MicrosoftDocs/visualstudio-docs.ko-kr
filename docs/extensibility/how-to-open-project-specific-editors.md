---
title: '방법: 프로젝트 관련 편집기 열기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 22106ea09f86e3d61fe7aaa6e86e6e99c002f32d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905800"
---
# <a name="how-to-open-project-specific-editors"></a>방법: 프로젝트 관련 편집기 열기
프로젝트에 의해 열리는 항목 파일이 기본적으로 해당 프로젝트의 특정 편집기에 바인딩된 경우 프로젝트는 프로젝트별 편집기를 사용 하 여 파일을 열어야 합니다. 편집기를 선택 하기 위해 IDE의 메커니즘으로 파일을 위임할 수 없습니다. 예를 들어 표준 비트맵 편집기를 사용 하는 대신이 프로젝트 관련 편집기 옵션을 사용 하 여 프로젝트에 고유한 파일의 정보를 인식 하는 특정 비트맵 편집기를 지정할 수 있습니다.

 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 특정 프로젝트에서 파일을 열어야 하는 경우 메서드를 호출 합니다. 자세한 내용은 [파일 열기 명령을 사용 하 여 파일 표시](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)를 참조 하세요. 프로젝트 `OpenItem` 관련 편집기를 사용 하 여 프로젝트에서 파일을 열 수 있도록 메서드를 구현 하려면 다음 지침을 따르십시오.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>프로젝트별 편집기를 사용 하 여 OpenItem 메서드를 구현 하려면

1. ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> ) 메서드를 호출 `RDT_EditLock` 하 여 파일 (문서 데이터 개체)이 이미 열려 있는지 여부를 확인 합니다.

    > [!NOTE]
    > 문서 데이터 및 문서 뷰 개체에 대 한 자세한 내용은 [사용자 지정 편집기의 문서 데이터 및 문서 뷰](../extensibility/document-data-and-document-view-in-custom-editors.md)를 참조 하세요.

2. 파일이 이미 열려 있는 경우에는 메서드를 호출 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 고 매개 변수에 IDO_ActivateIfOpen 값을 지정 하 여 파일을 resurface 합니다 `grfIDO` .

     파일이 열려 있고 문서를 호출 하는 프로젝트가 아닌 프로젝트에서 소유 하 고 있는 경우 사용자에 게 열려 있는 편집기가 다른 프로젝트에서 발생 하는 것으로 표시 되는 경고가 표시 됩니다. 그러면 파일 창이 표시 됩니다.

3. 텍스트 버퍼 (문서 데이터 개체)가 이미 열려 있는 상태에서 다른 뷰를 연결 하려는 경우 해당 뷰를 연결 해야 합니다. 프로젝트에서 뷰 (문서 뷰 개체)를 인스턴스화하는 권장 방법은 다음과 같습니다.

    1. `QueryService`서비스에서를 호출 하 여 인터페이스에 대 한 포인터를 <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> .

    2. 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 하 여 문서 뷰 클래스의 인스턴스를 만듭니다.

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>문서 뷰 개체를 지정 하 여 메서드를 호출 합니다.

     이 메서드는 문서 창에서 문서 뷰 개체를 사이트 합니다.

5. 또는 메서드에 대 한 적절 한 호출을 수행 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> .

     이 시점에서 뷰를 완전히 초기화 하 여 열 수 있도록 준비 해야 합니다.

6. 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 하 여 뷰를 표시 하 고 엽니다.

## <a name="see-also"></a>추가 정보
- [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)
- [방법: 열려 있는 문서에 대 한 편집기 열기](../extensibility/how-to-open-editors-for-open-documents.md)
