---
title: '방법: 표준 편집기 열기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 792ac8a0859481fd97b2eaee4bd66753f0460a37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204128"
---
# <a name="how-to-open-standard-editors"></a>방법: 표준 편집기 열기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

표준 편집기를 열면 파일에 프로젝트별 편집기를 지정 하는 대신 IDE에서 지정 된 파일 형식에 대 한 표준 편집기를 확인할 수 있습니다.  
  
 다음 절차를 완료 하 여 메서드를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 합니다. 이렇게 하면 표준 편집기에서 프로젝트 파일이 열립니다.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>표준 편집기를 사용 하 여 OpenItem 메서드를 구현 하려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>( `RDT_EditLock` )를 호출 하 여 문서 데이터 개체 파일이 이미 열려 있는지 여부를 확인 합니다.  
  
2. 파일이 이미 열려 있는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 매개 변수에 값을 지정 하 여 메서드를 호출 하 여 파일을 resurface `IDO_ActivateIfOpen` `grfIDO` 합니다.  
  
     파일이 열려 있고 문서를 호출 하는 프로젝트가 아닌 다른 프로젝트에서 소유 하 고 있는 경우에는 열려 있는 편집기가 다른 프로젝트에서 발생 하는 경고를 프로젝트에 받게 됩니다. 그러면 파일 창이 표시 됩니다.  
  
3. 문서가 열려 있지 않거나 실행 중인 문서 테이블에 없으면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드 ()를 호출 `OSE_ChooseBestStdEditor` 하 여 파일에 대 한 표준 편집기를 엽니다.  
  
     메서드를 호출 하면 IDE에서 다음 작업을 수행 합니다.  
  
    1. IDE는 레지스트리에서 편집기/{guidEditorType}/확장 하위 키를 검색 하 여 파일을 열 수 있는 편집기를 확인 하 고이 작업을 수행할 때 가장 높은 우선 순위를 갖습니다.  
  
    2. IDE는 파일을 열 수 있는 편집기를 확인 한 후를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 합니다. 편집기의이 메서드를 구현 하면 IDE에서 새로 열린 문서를 호출 하 고 사이트에 연결 하는 데 필요한 정보가 반환 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .  
  
    3. 마지막으로 IDE는와 같은 일반적인 지 속성 인터페이스를 사용 하 여 문서를 로드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 합니다.  
  
    4. 이전에 IDE에서 계층 또는 계층 항목을 사용할 수 있는 것으로 확인 한 경우 프로젝트에서 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 메서드 호출을 통해 다시 전달 되는 프로젝트 수준 컨텍스트 포인터를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .  
  
4. 편집기에서 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 프로젝트의 컨텍스트를 가져올 수 있도록 하려면 ide에서 프로젝트에 대해를 호출할 때 ide에 대 한 포인터를 반환 합니다.  
  
     이 단계를 수행 하면 프로젝트에서 편집기에 추가 서비스를 제공할 수 있습니다.  
  
     문서 뷰 또는 문서 뷰 개체가 창 프레임에 성공적으로 배치 된 경우를 호출 하 여 개체가 데이터를 사용 하 여 초기화 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)   
 [방법: 프로젝트 관련 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)   
 [방법: 열려 있는 문서에 대 한 편집기 열기](../extensibility/how-to-open-editors-for-open-documents.md)   
 [파일 열기 명령을 사용하여 파일 표시](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
