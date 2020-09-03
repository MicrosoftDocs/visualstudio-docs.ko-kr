---
title: 문서 테이블 실행 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea32df892efa47c91d8292bdc9065080318a059
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155552"
---
# <a name="running-document-table"></a>문서 테이블 실행
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE는 현재 열려 있는 모든 문서 목록을 RDT (실행 중인 문서 테이블) 라는 내부 구조에 유지 합니다. 이 목록에는 이러한 문서를 현재 편집 하 고 있는지 여부에 관계 없이 메모리에 열려 있는 모든 문서가 포함 됩니다. 문서는 프로젝트 또는 주 프로젝트 파일 (예: .vcxproj 파일)의 파일을 포함 하 여 유지 되는 모든 항목입니다.  
  
## <a name="elements-of-the-running-document-table"></a>실행 중인 문서 테이블의 요소  
 실행 중인 문서 테이블에는 다음 항목이 포함 되어 있습니다.  
  
|요소|설명|  
|-------------|-----------------|  
|문서 모니커|문서 데이터 개체를 고유 하 게 식별 하는 문자열입니다. 이는 파일을 관리 하는 프로젝트 시스템의 절대 파일 경로입니다 (예: C:\MyProject\MyFile). 이 문자열은 데이터베이스의 저장 프로시저와 같이 파일 시스템 이외의 저장소에 저장 된 프로젝트에도 사용 됩니다. 이 경우 프로젝트 시스템은 문서를 저장 하는 방법을 결정 하기 위해 인식 하 고 구문 분석할 수 있는 고유한 문자열을 만들 수 있습니다.|  
|계층 소유자|인터페이스로 표시 되는 문서를 소유 하는 hierarchy 개체입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .|  
|항목 ID|계층 구조 내의 특정 항목에 대 한 항목 식별자입니다. 이 값은이 문서를 소유 하는 계층의 모든 문서에서 고유 하지만이 값은 여러 계층에서 고유 하지 않을 수 있습니다.|  
|문서 데이터 개체|최소한 다음은입니다. `IUnknown`<br /><br /> 이름입니다. IDE에는 `IUnknown` 사용자 지정 편집기의 문서 데이터 개체에 대 한 인터페이스를 벗어나는 특정 인터페이스가 필요 하지 않습니다. 그러나 표준 편집기의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 프로젝트에서 파일 지 속성 호출을 처리 하려면 편집기의 인터페이스 구현이 필요 합니다. 자세한 내용은 [표준 문서 저장](../../extensibility/internals/saving-a-standard-document.md)을 참조 하세요.|  
|플래그|항목이 저장 되는지 여부, 읽기 또는 편집 잠금이 적용 되는지 여부를 제어 하는 플래그는 항목이 RDT에 추가 될 때 지정할 수 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 열거형을 참조하세요.|  
|잠금 수 편집|편집 잠금 수입니다. 편집 잠금은 일부 편집기에서 편집을 위해 문서를 열어 놓은 것을 나타냅니다. 편집 잠금 수가 0으로 전환 되 면 문서를 저장 하 라는 메시지가 사용자에 게 표시 됩니다 (수정 된 경우). 예를 들어 **새 창** 명령을 사용 하 여 편집기에서 문서를 열 때마다 rdt의 해당 문서에 대 한 편집 잠금이 추가 됩니다. 편집 잠금을 설정 하려면 문서에 계층 또는 항목 ID가 있어야 합니다.|  
|읽기 잠금 수|읽기 잠금 수입니다. 읽기 잠금은 마법사와 같은 몇 가지 메커니즘을 통해 문서를 읽는 중임을 나타냅니다. 읽기 잠금은 문서를 편집할 수 없음을 나타내는 동안 RDT에 연결 된 문서를 유지 합니다. 문서에 계층 또는 항목 ID가 없는 경우에도 읽기 잠금을 설정할 수 있습니다. 이 기능을 사용 하면 메모리에서 문서를 열고 계층에서 문서를 소유 하지 않고 RDT에 입력할 수 있습니다. 이 기능은 거의 사용 되지 않습니다.|  
|잠금 표시자|인터페이스의 인스턴스입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> . 잠금 표시자는 편집기 외부에서 문서를 열고 편집 하는 마법사와 같은 기능을 통해 구현 됩니다. 잠금 보유자를 사용 하면 문서에 편집 잠금을 추가 하 여 문서를 편집 하는 동안 문서를 닫을 수 없습니다. 일반적으로 편집 잠금은 문서 창 (즉, 편집기)에 의해서만 추가 됩니다.|  
  
 RDT의 각 항목에는 고유한 계층 또는 항목 ID가 연결 되어 있으며,이는 일반적으로 프로젝트의 한 노드에 해당 합니다. 편집에 사용할 수 있는 모든 문서는 일반적으로 계층이 소유 합니다. RDT에서 수행 된 항목은 현재 편집 중인 문서 데이터 개체를 소유 하 고 있는 프로젝트 또는 더 정확한 계층 구조를 제어 합니다. IDE는 RDT의 정보를 사용 하 여 한 번에 둘 이상의 프로젝트에서 문서를 열지 못하도록 방지할 수 있습니다.  
  
 또한 계층은 데이터의 지 속성을 제어 하 고 RDT의 정보를 사용 하 여 **저장** 및 다른 **이름으로 저장** 대화 상자를 업데이트 합니다. 사용자가 문서를 수정 하 고 **파일** 메뉴에서 **끝내기** 명령을 선택 하면 IDE에서 **변경 내용 저장** 대화 상자를 표시 하 여 현재 수정 된 모든 프로젝트 및 프로젝트 항목을 표시 합니다. 이를 통해 사용자는 저장할 문서를 선택할 수 있습니다. 저장할 문서 목록 (즉, 변경 내용이 있는 문서)은 RDT에서 생성 됩니다. 응용 프로그램을 종료할 때 **변경 내용 저장** 대화 상자에 표시 될 것으로 표시 되는 항목은 rdt에 레코드를 포함 해야 합니다. RDT는 저장할 문서와 각 문서에 대 한 플래그 항목에 지정 된 값을 사용 하 여 저장 작업에 대 한 메시지를 사용자에 게 표시할지 여부를 조정 합니다. RDT 플래그에 대 한 자세한 내용은 열거형을 참조 하세요 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> .  
  
## <a name="edit-locks-and-read-locks"></a>잠금 편집 및 읽기 잠금  
 잠금 편집 및 읽기 잠금이 RDT에 있습니다. 문서 창은 편집 잠금을 증가 시키고 감소 시킵니다. 따라서 사용자가 새 문서 창을 열면 편집 잠금 수가 1 씩 증가 합니다. 편집 잠금 수가 0에 도달 하면 계층 구조는 연결 된 문서에 대 한 데이터를 유지 하거나 저장 하도록 신호를 전달 합니다. 그런 다음 계층은 파일 또는 리포지토리의 항목으로 유지 하는 등의 방법으로 데이터를 유지할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>인터페이스에서 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 편집 잠금 및 읽기 잠금을 추가 하 고 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 이러한 잠금을 제거할 수 있습니다.  
  
 일반적으로 편집기의 문서 창이 인스턴스화되면 창 프레임에서 RDT의 문서에 대 한 편집 잠금을 자동으로 추가 합니다. 그러나 표준 문서 창을 사용 하지 않는 문서 (즉, 인터페이스를 구현 하지 않음)의 사용자 지정 보기를 만드는 경우에는 사용자 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 고유의 편집 잠금을 설정 해야 합니다. 예를 들어 마법사에서는 편집기에서 열지 않고 문서를 편집 합니다. 문서 잠금을 마법사와 유사한 엔터티에 의해 열리도록 하려면 이러한 엔터티가 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> . 문서 잠금 보유자를 등록 하려면 메서드를 호출 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 고 구현에 전달 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 합니다. 이렇게 하면 문서 잠금 보유자가 RDT에 추가 됩니다. 문서 잠금 보유자를 구현 하는 또 다른 시나리오는 특수 도구 창을 통해 문서를 여는 경우입니다. 이 경우 도구 창을 닫을 수 없습니다. 그러나 RDT에서 문서 잠금 표시자로 등록 하면 IDE는 메서드의 구현을 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> 하 여 문서를 닫도록 메시지를 표시할 수 있습니다.  
  
## <a name="other-uses-of-the-running-document-table"></a>실행 중인 문서 테이블의 기타 사용  
 IDE의 다른 엔터티는 RDT를 사용 하 여 문서에 대 한 정보를 가져옵니다. 예를 들어 소스 제어 관리자는 파일의 최신 버전을 가져온 후 편집기에서 문서를 다시 로드 하도록 시스템에 지시 하는 RDT를 사용 합니다. 이렇게 하기 위해 소스 제어 관리자는 RDT의 파일을 조회 하 여 열려 있는지 확인 합니다. 인 경우 소스 제어 관리자는 먼저 계층 구조가 메서드를 구현 하는지 확인 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> . 프로젝트에서 메서드를 구현 하지 않는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 소스 제어 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 문서 데이터 개체에서 직접 메서드를 구현 하는지 확인 합니다.  
  
 또한 사용자가 해당 문서를 요청 하는 경우 IDE는 RDT를 사용 하 여 열린 문서를 resurface (앞으로 가져오기) 합니다. 자세한 내용은 [파일 열기 명령을 사용 하 여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)를 참조 하세요. 파일이 RDT에서 열려 있는지 확인 하려면 다음을 수행 합니다.  
  
- 문서 모니커 (전체 문서 경로)를 쿼리하여 항목이 열려 있는지 확인 합니다.  
  
- 계층 또는 항목 ID를 사용 하 여 프로젝트 시스템에 전체 문서 경로를 요청한 다음 RDT에서 항목을 확인 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [RDT_ReadLock 사용](../../extensibility/internals/rdt-readlock-usage.md)   
 [지속성 및 실행 중인 문서 테이블](../../extensibility/internals/persistence-and-the-running-document-table.md)
