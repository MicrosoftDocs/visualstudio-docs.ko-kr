---
title: '방법: 표준 편집자 열기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710794"
---
# <a name="how-to-open-standard-editors"></a>방법: 표준 편집기 열기
표준 편집기를 열 때 IDE가 파일에 대한 프로젝트별 편집기 지정 대신 지정된 파일 형식에 대한 표준 편집기확인을 하도록 합니다.

 메서드를 구현 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 다음 절차를 완료 합니다. 그러면 표준 편집기에서 프로젝트 파일이 열립니다.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>표준 편집기로 OpenItem 메서드를 구현하려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ()`RDT_EditLock`를 호출하여 문서 데이터 개체 파일이 이미 열려 있는지 확인합니다.

2. 파일이 이미 열려 있는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> `IDO_ActivateIfOpen` `grfIDO` 메서드를 호출하여 매개 변수에 대한 값을 지정하여 파일을 다시 표시합니다.

     파일이 열려 있고 문서가 호출 프로젝트와 다른 프로젝트에서 소유하는 경우 프로젝트에서 열려 있는 편집기는 다른 프로젝트에서 온 것이라는 경고를 받습니다. 그런 다음 파일 창이 표시됩니다.

3. 문서가 열려 있지 않거나 실행 중인 문서 테이블에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 없는`OSE_ChooseBestStdEditor`경우 메서드 () 를 호출하여 파일에 대한 표준 편집기를 엽니다.

     메서드를 호출하면 IDE는 다음 작업을 수행합니다.

    1. IDE는 레지스트리의 편집자/{guidEditorType}/확장 하위 키를 검사하여 파일을 열 수 있는 편집기를 결정하고 이 작업을 수행하는 데 가장 높은 우선 순위를 갖습니다.

    2. IDE가 파일을 열 수 있는 편집기(편집기)를 결정한 후 IDE는 을 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 이 메서드를 편집기의 구현은 IDE가 새로 연 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 문서를 호출하고 사이트를 지정하는 데 필요한 정보를 반환합니다.

    3. 마지막으로 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>와 같은 일반적인 지속성 인터페이스를 사용하여 문서를 로드합니다.

    4. IDE가 이전에 계층 또는 계층 항목을 사용할 수 있다고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 결정한 경우 IDE는 프로젝트에서 메서드를 호출하여 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 메서드 호출을 사용하여 프로젝트 수준 컨텍스트 포인터를 다시 전달합니다.

4. 편집기에서 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 프로젝트에서 컨텍스트를 얻을 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 있도록 하려면 IDE가 프로젝트를 호출할 때 IDE에 대한 포인터를 반환합니다.

     이 단계를 수행하면 프로젝트가 편집기에게 추가 서비스를 제공할 수 있습니다.

     문서 뷰 또는 문서 뷰 개체가 창 프레임에 성공적으로 사이트된 경우 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>을 호출하여 해당 데이터로 초기화됩니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 프로젝트별 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)
- [방법: 열린 문서에 대한 편집기 열기](../extensibility/how-to-open-editors-for-open-documents.md)
- [파일 열기 명령을 사용하여 파일 표시](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
