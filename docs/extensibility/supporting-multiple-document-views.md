---
title: 여러 문서 보기 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699546"
---
# <a name="supporting-multiple-document-views"></a>여러 문서 보기 지원
편집기에 대 한 별도의 문서 데이터 및 문서 뷰 개체를 만들어 문서에 대 한 뷰를 두 개 이상 제공할 수 있습니다. 추가 문서 보기가 유용한 경우는 다음과 같습니다.

- 새 창 지원: 편집기에서 동일한 형식의 뷰를 두 개 이상 제공 하 여 편집기에서 창이 이미 열려 있는 사용자가 **창** 메뉴에서 **새 창** 명령을 선택 하 여 새 창을 열 수 있도록 합니다.

- 폼 및 코드 보기 지원: 편집기에서 다양 한 형식의 뷰를 제공 하려고 합니다. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]예를 들어은 폼 뷰와 코드 뷰를 모두 제공 합니다.

  이에 대 한 자세한 내용은 Visual Studio 패키지 템플릿에서 만든 사용자 지정 편집기 프로젝트의 EditorFactory.cs 파일에서 CreateEditorInstance 프로시저를 참조 하세요. 이 프로젝트에 대 한 자세한 내용은 [연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)를 참조 하세요.

## <a name="synchronizing-views"></a>뷰 동기화
 여러 뷰를 구현할 때 문서 데이터 개체는 모든 보기를 데이터와 동기화 된 상태로 유지 하는 일을 담당 합니다. 에서 이벤트 처리 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 여러 뷰를 데이터와 동기화 할 수 있습니다.

 개체를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 여러 뷰를 동기화 하지 않는 경우 문서 데이터 개체에 대 한 변경 내용을 처리 하기 위해 고유한 이벤트 시스템을 구현 해야 합니다. 서로 다른 세분성 수준을 사용 하 여 여러 뷰를 최신 상태로 유지할 수 있습니다. 단일 보기에서 입력 하는 것과 같이 최대 세분성 설정을 사용 하면 다른 뷰가 즉시 업데이트 됩니다. 최소 세분성을 사용 하면 다른 보기는 활성화 될 때까지 업데이트 되지 않습니다.

## <a name="determining-whether-document-data-is-already-open"></a>문서 데이터가 이미 열려 있는지 여부 확인
 IDE (통합 개발 환경)의 RDT (실행 문서 테이블)는 다음 다이어그램에 표시 된 것 처럼 문서에 대 한 데이터가 이미 열려 있는지 여부를 추적 하는 데 도움이 됩니다.

 ![Docdataview 그래픽](../extensibility/media/docdataview.gif "Docdataview") 여러 뷰

 기본적으로 각 뷰 (document view 개체)는 자체 창 프레임 ()에 포함 되어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 있습니다. 그러나 이미 언급 했 듯이 문서 데이터는 여러 뷰에 표시 될 수 있습니다. 이를 사용 하도록 설정 하기 위해 Visual Studio는 해당 문서가 편집기에 이미 열려 있는지 여부를 확인 하기 위해 RDT를 확인 합니다. IDE가를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 하 여 편집기를 만들 때 매개 변수에서 반환 되는 NULL이 아닌 값은 `punkDocDataExisting` 문서가 이미 다른 편집기에서 열려 있음을 나타냅니다. RDT 함수를 실행 하는 방법에 대 한 자세한 내용은 [Document Table 실행](../extensibility/internals/running-document-table.md)을 참조 하세요.

 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 에 반환 된 문서 데이터 개체를 검사 `punkDocDataExisting` 하 여 문서 데이터가 편집기에 적합 한지 여부를 확인 합니다. 예를 들어 html 데이터만 HTML 편집기에서 표시 해야 합니다. 적절 한 경우 편집기 팩터리는 데이터에 대 한 두 번째 뷰를 제공 해야 합니다. `punkDocDataExisting`매개 변수가이 아니면 `NULL` 문서 데이터 개체가 다른 편집기에서 열려 있거나 동일한 편집기를 사용 하 여 다른 보기에서 문서 데이터를 이미 연 것일 수 있습니다. 문서 데이터가 편집기 팩터리에서 지원 하지 않는 다른 편집기에서 열려 있으면 Visual Studio에서 편집기 팩터리를 열지 못합니다. 자세한 내용은 [방법: 문서 데이터에 보기 연결](../extensibility/how-to-attach-views-to-document-data.md)을 참조 하세요.
