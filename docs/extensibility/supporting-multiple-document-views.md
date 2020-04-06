---
title: 여러 문서 보기 지원 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699546"
---
# <a name="supporting-multiple-document-views"></a>여러 문서 보기 지원
편집기용 별도의 문서 데이터 및 문서 보기 개체를 만들어 문서보기를 두 개 이상 제공할 수 있습니다. 추가 문서 보기가 유용한 경우는 다음과 같습니다.

- 새 창 지원: 편집기에서 이미 열려 있는 창이 있는 사용자가 **창** 메뉴에서 **새 창** 명령을 선택하여 새 창을 열 수 있도록 편집기에서 동일한 형식의 두 개 이상의 보기를 제공하려고 합니다.

- 양식 및 코드 보기 지원: 편집기에서 다양한 형식의 보기를 제공하려고 합니다. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]예를 들어 양식 보기와 코드 보기를 모두 제공합니다.

  이에 대한 자세한 내용은 Visual Studio 패키지 템플릿에서 만든 사용자 지정 편집기 프로젝트의 EditorFactory.cs 파일의 CreateEditorInstance 프로시저를 참조하십시오. 이 프로젝트에 대한 자세한 내용은 [연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)를 참조하십시오.

## <a name="synchronizing-views"></a>뷰 동기화
 여러 뷰를 구현할 때 문서 데이터 개체는 모든 뷰를 데이터와 동기화된 상태로 유지합니다. 이벤트 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 처리 인터페이스를 사용하여 여러 뷰를 데이터와 동기화할 수 있습니다.

 개체를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 사용하여 여러 뷰를 동기화하지 않는 경우 문서 데이터 개체에 대한 변경 내용을 처리하기 위해 고유한 이벤트 시스템을 구현해야 합니다. 다양한 수준의 세분성을 사용하여 여러 뷰를 최신 상태로 유지할 수 있습니다. 한 뷰를 입력하면 다른 뷰가 즉시 업데이트됩니다. 최소 세분성을 사용하면 다른 뷰가 활성화될 때까지 업데이트되지 않습니다.

## <a name="determining-whether-document-data-is-already-open"></a>문서 데이터가 이미 열려 있는지 확인
 통합 개발 환경(IDE)에서 실행 중인 문서 테이블(RDT)은 다음 다이어그램과 같이 문서의 데이터가 이미 열려 있는지 여부를 추적하는 데 도움이 됩니다.

 ![닥데이터뷰 그래픽](../extensibility/media/docdataview.gif "문서 데이터 보기") 여러 뷰

 기본적으로 각 뷰(문서 뷰 개체)는 자체 창<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>프레임()에 포함됩니다. 그러나 이미 언급했듯이 문서 데이터는 여러 뷰에 표시될 수 있습니다. 이를 위해 Visual Studio는 RDT를 검사하여 해당 문서가 편집기에서 이미 열려 있는지 확인합니다. IDE가 편집기를 만들기 위해 호출할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 때 `punkDocDataExisting` 매개 변수에 반환된 NULL이 아닌 값은 문서가 다른 편집기에서 이미 열려 있음을 나타냅니다. RDT가 작동하는 방식에 대한 자세한 내용은 [문서 테이블 실행](../extensibility/internals/running-document-table.md)을 참조하십시오.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 구현에서 반환된 `punkDocDataExisting` 문서 데이터 개체를 검사하여 문서 데이터가 편집기에 적합한지 확인합니다. (예를 들어 HTML 편집기에서 HTML 데이터만 표시해야 합니다.) 적절한 경우 편집기 팩터리는 데이터에 대한 두 번째 보기를 제공해야 합니다. 매개 `punkDocDataExisting` 변수가 `NULL`아닌 경우 문서 데이터 개체가 다른 편집기에서 열려 있거나 문서 데이터가 동일한 편집기의 다른 뷰에서 이미 열려 있는 것일 수 있습니다. 편집기 팩터리에서 지원하지 않는 다른 편집기에서 문서 데이터가 열려 있으면 Visual Studio에서 편집기 팩터리를 열지 못합니다. 자세한 내용은 [방법: 뷰를 문서 데이터에 첨부하는](../extensibility/how-to-attach-views-to-document-data.md)방법을 참조하십시오.
