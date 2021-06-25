---
title: 문서 테이블 | 실행 Microsoft Docs
description: Visual Studio IDE가 열려 있는 모든 문서를 메모리에 포함하는 실행 중인 문서 테이블을 유지 관리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d260534d58853afc6b84ba484eb3a806250e2aa6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900410"
---
# <a name="running-document-table"></a>문서 테이블 실행
IDE는 실행 중인 문서 테이블(RDT)이라는 내부 구조에서 현재 열려 있는 모든 문서의 목록을 유지 관리합니다. 이 목록에는 이러한 문서가 현재 편집 중인지 여부에 관계없이 메모리에 열려 있는 모든 문서가 포함됩니다. 문서는 프로젝트 또는 주 프로젝트 파일(예: .vcxproj 파일)의 파일을 포함하여 유지되는 모든 항목입니다.

## <a name="elements-of-the-running-document-table"></a>실행 중인 문서 테이블의 요소
 실행 중인 문서 테이블에는 다음 항목이 포함되어 있습니다.

|요소|설명|
|-------------|-----------------|
|문서 모니커|문서 데이터 개체를 고유하게 식별하는 문자열입니다. 이는 파일을 관리하는 프로젝트 시스템의 절대 파일 경로입니다(예: C:\MyProject\MyFile). 이 문자열은 데이터베이스의 저장 프로시저와 같이 파일 시스템 이외의 저장소에 저장된 프로젝트에도 사용됩니다. 이 경우 프로젝트 시스템은 문서를 저장하는 방법을 결정하기 위해 인식하고 구문 분석할 수 있는 고유한 문자열을 고안할 수 있습니다.|
|계층 소유자|인터페이스로 표현되는 문서를 소유하는 계층 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체입니다.|
|항목 ID|계층 내의 특정 항목에 대한 항목 식별자입니다. 이 값은 이 문서를 소유하는 계층 구조의 모든 문서에서 고유하지만 이 값이 서로 다른 계층에서 고유하지는 않습니다.|
|문서 데이터 개체|최소한 입니다. `IUnknown`<br /><br /> 이름입니다. IDE에는 사용자 지정 편집기 문서 데이터 개체에 대한 인터페이스 이외의 특정 인터페이스가 필요하지 `IUnknown` 않습니다. 그러나 표준 편집기의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 프로젝트에서 파일 지속성 호출을 처리하려면 편집기의 인터페이스 구현이 필요합니다. 자세한 내용은 [표준 문서 저장을 참조하세요.](../../extensibility/internals/saving-a-standard-document.md)|
|플래그|RDT에 항목을 추가할 때 문서 저장 여부, 읽기 또는 편집 잠금 적용 여부 등을 제어하는 플래그를 지정할 수 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 열거형을 참조하세요.|
|잠금 수 편집|편집 잠금 수입니다. 편집 잠금은 일부 편집기에서 편집을 위해 열려 있는 문서가 있음을 나타냅니다. 편집 잠금 수가 0으로 전환되면 수정된 경우 문서를 저장하라는 메시지가 사용자에게 표시됩니다. 예를 들어 **새 창** 명령을 사용하여 편집기에서 문서를 열 때마다 RDT에서 해당 문서에 대한 편집 잠금이 추가됩니다. 편집 잠금을 설정하려면 문서에 계층 또는 항목 ID가 있어야 합니다.|
|읽기 잠금 수|읽기 잠금 수입니다. 읽기 잠금은 마법사와 같은 일부 메커니즘을 통해 문서를 읽고 있음을 나타냅니다. 읽기 잠금은 문서를 편집할 수 없음을 나타내는 동시에 RDT에 문서가 유지됩니다. 문서에 계층 또는 항목 ID가 없는 경우에도 읽기 잠금을 설정할 수 있습니다. 이 기능을 사용하면 문서를 계층 구조에서 소유하지 않고도 메모리에서 문서를 열고 RDT에 입력할 수 있습니다. 이 기능은 거의 사용되지 않습니다.|
|잠금 소유자|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>인터페이스의 인스턴스입니다. 잠금 보유자는 편집기 외부에서 문서를 열고 편집하는 마법사와 같은 기능에 의해 구현됩니다. 잠금 소유자를 사용하면 문서가 편집되는 동안 문서가 닫히는 것을 방지하기 위해 문서에 편집 잠금을 추가할 수 있습니다. 일반적으로 편집 잠금은 문서 창(즉, 편집기)에서만 추가됩니다.|

 RDT의 각 항목에는 일반적으로 프로젝트의 한 노드에 해당하는 고유한 계층 또는 항목 ID가 연결되어 있습니다. 편집에 사용할 수 있는 모든 문서는 일반적으로 계층에서 소유합니다. RDT에서 만든 항목은 현재 편집 중인 문서 데이터 개체를 소유하는 프로젝트 또는 보다 정확하게 어떤 계층을 제어합니다. RDT의 정보를 사용하여 IDE는 한 번에 두 개 이상의 프로젝트에서 문서를 열지 못하도록 방지할 수 있습니다.

 또한 계층은 데이터의 지속성을 제어하고 RDT의 정보를 사용하여 다른 이름으로 **저장** 및 **저장** 대화 상자를 업데이트합니다. 사용자가 문서를 수정한 다음 **파일** 메뉴에서 **끝내기** 명령을 선택하면 IDE에서 변경 **내용 저장** 대화 상자를 표시하여 현재 수정된 모든 프로젝트 및 프로젝트 항목을 표시합니다. 이렇게 하면 사용자가 저장할 문서를 선택할 수 있습니다. 저장할 문서 목록(즉, 변경 내용이 있는 문서)은 RDT에서 생성됩니다. 애플리케이션을 종료할 때 **변경 내용 저장** 대화 상자에 표시되어야 하는 항목은 RDT에 레코드가 있어야 합니다. RDT는 저장되는 문서와 각 문서의 Flags 항목에 지정된 값을 사용하여 저장 작업에 대한 메시지가 사용자에게 표시되는지 여부를 조정합니다. RDT 플래그에 대한 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 열거형을 참조하세요.

## <a name="edit-locks-and-read-locks"></a>잠금 및 읽기 잠금 편집
 잠금 편집 및 읽기 잠금은 RDT에 상주합니다. 문서 창은 편집 잠금을 증가시키고 감소합니다. 따라서 사용자가 새 문서 창을 열면 편집 잠금 수가 1씩 증가합니다. 편집 잠금 수가 0에 도달하면 계층 구조에 연결된 문서에 대한 데이터를 유지하거나 저장하라는 신호가 표시됩니다. 그런 다음 계층은 파일 또는 리포지토리의 항목으로 유지를 포함하여 어떤 방식으로든 데이터를 유지할 수 있습니다. 인터페이스에서 메서드를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> 편집 잠금 및 읽기 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 잠금을 추가하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 메서드를 사용하여 이러한 잠금을 제거할 수 있습니다.

 일반적으로 편집기용 문서 창이 인스턴스화되면 창 프레임은 RDT의 문서에 대한 편집 잠금을 자동으로 추가합니다. 그러나 표준 문서 창을 사용하지 않는 문서의 사용자 지정 뷰를 만드는 경우(즉, 인터페이스를 구현하지 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 않음) 고유한 편집 잠금을 설정해야 합니다. 예를 들어 마법사에서 문서는 편집기에서 열리지 않고 편집됩니다. 마법사 및 유사한 엔터티에서 문서 잠금을 열려면 이러한 엔터티는 인터페이스를 구현해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 합니다. 문서 잠금 소유자를 등록하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 메서드를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 구현을 전달합니다. 이렇게 하면 문서 잠금 소유자가 RDT에 추가됩니다. 문서 잠금 소유자를 구현하는 또 다른 시나리오는 특수 도구 창을 통해 문서를 여는 경우입니다. 이 경우 도구 창에서 문서를 닫을 수 없습니다. 그러나 RDT에서 문서 잠금 소유자로 등록하면 IDE에서 메서드의 구현을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> 호출하여 문서를 닫도록 요청할 수 있습니다.

## <a name="other-uses-of-the-running-document-table"></a>실행 중인 문서 테이블의 기타 사용
 IDE의 다른 엔터티는 RDT를 사용하여 문서에 대한 정보를 얻습니다. 예를 들어 소스 제어 관리자는 RDT를 사용하여 최신 버전의 파일을 가져온 후 편집기에서 문서를 다시 로드하도록 시스템에 지시합니다. 이를 위해 소스 제어 관리자는 RDT의 파일을 검색하여 파일이 열려 있는지 확인합니다. 이 경우 소스 제어 관리자는 먼저 계층이 메서드를 구현하는지 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 확인합니다. 프로젝트가 메서드를 구현하지 않는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 소스 제어 관리자는 문서 데이터 개체에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 메서드의 구현을 직접 확인합니다.

 또한 사용자가 해당 문서를 요청하는 경우 IDE는 RDT를 사용하여 열려 있는 문서를 다시 표시(전면으로 가져오기)합니다. 자세한 내용은 [파일 열기 명령을 사용하여 파일 표시 를 참조하세요.](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md) 파일이 RDT에서 열려 있는지 확인하려면 다음을 수행합니다.

- 문서 모니커(즉, 전체 문서 경로)를 쿼리하여 항목이 열려 있는지 확인합니다.

- 계층 또는 항목 ID를 사용하여 프로젝트 시스템에 전체 문서 경로를 요청한 다음 RDT에서 항목을 조회합니다.

## <a name="see-also"></a>참조
- [RDT_ReadLock 사용법](../../extensibility/internals/rdt-readlock-usage.md)
- [지속성 및 실행 중인 문서 테이블](../../extensibility/internals/persistence-and-the-running-document-table.md)
