---
title: '연습: 사용자 지정 편집기에 기능 추가 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0340b89ed87872833f554fb00e24aca2f4759f3
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583595"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>연습: 사용자 지정 편집기에 기능 추가
사용자 지정 편집기를 만든 후 추가 기능을 추가할 수 있습니다.

## <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage에 대 한 편집기를 만들려면

1. Visual Studio 패키지 프로젝트 템플릿을 사용 하 여 사용자 지정 편집기를 만듭니다.

     자세한 내용은 [연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)를 참조 하세요.

2. 편집기에서 단일 뷰나 여러 뷰를 지원 하도록 할지 여부를 결정 합니다.

     **새 창** 명령을 지원 하거나 폼 뷰와 코드 뷰를 포함 하는 편집기의 경우 별도의 문서 데이터 개체 및 문서 뷰 개체가 필요 합니다. 단일 뷰를 지 원하는 편집기에서는 문서 데이터 개체와 문서 뷰 개체를 같은 개체에 대해 구현할 수 있습니다.

     여러 뷰의 예는 [다중 문서 뷰 지원](../extensibility/supporting-multiple-document-views.md)을 참조 하세요.

3. 인터페이스를 설정 하 여 편집기 팩터리를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 합니다.

     자세한 내용은 [편집기 팩터리](../vs-2015/extensibility/editor-factories.md?view=vs-2015&preserve-view=true)를 참조 하세요.

4. 편집기에서 내부 활성화 또는 간단한 포함을 사용 하 여 문서 뷰 개체 창을 관리할 지 여부를 결정 합니다.

     간단한 포함 편집기 창에서는 표준 문서 뷰를 호스팅하고, 내부 활성화 편집기 창에서는 ActiveX 컨트롤이 나 기타 활성 개체를 문서 뷰로 호스팅합니다. 자세한 내용은 [간소화 된 포함](../extensibility/simplified-embedding.md) 및 [내부 활성화](../vs-2015/misc/in-place-activation.md?view=vs-2015&preserve-view=true)를 참조 하세요.

5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>명령을 처리 하는 인터페이스를 구현 합니다.

6. 문서 지 속성 및 외부 파일 변경에 대 한 응답 제공:

    1. 파일을 유지 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 편집기의 문서 데이터 개체에서 및를 구현 합니다.

    2. 외부 파일 변경 내용에 응답 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 편집기의 문서 데이터 개체에서 및를 구현 합니다.

        > [!NOTE]
        > 에 `QueryService` 대 한 포인터를 가져오려면를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> `IVsFileChangeEx` 합니다.

7. 소스 코드 제어를 사용 하 여 문서 편집 이벤트를 조정 합니다. 다음 단계를 수행합니다.

    1. 에서를 호출 하 여에 대 한 포인터를 가져옵니다 `IVsQueryEditQuerySave2` `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .

    2. 첫 번째 편집 이벤트가 발생 하는 경우 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 합니다.

         이 메서드는 파일을 체크 아웃 하지 않은 경우 사용자에 게 파일을 체크 아웃 하 라는 메시지를 표시 합니다. 오류를 방지 "파일을 체크 아웃 하지 않았습니다." 조건을 처리 해야 합니다.

    3. 마찬가지로, 파일을 저장 하기 전에 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 합니다.

         이 메서드는 파일이 저장 되지 않았거나 마지막으로 저장 한 이후 변경 된 경우 파일을 저장 하 라는 메시지를 표시 합니다.

8. 편집기에서 선택한 텍스트에 대 한 속성을 표시 하려면 **속성** 창을 사용 하도록 설정 합니다. 다음 단계를 수행합니다.

    1. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>텍스트 선택이 변경 될 때마다를 호출 하 여의 구현에 전달 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 합니다.

    2. `QueryService`서비스에서 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 를 호출 하 여에 대 한 포인터를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

9. 사용자가 편집기와 **도구 상자**사이에서 또는 외부 편집기 (예: Microsoft Word)와 **도구 상자**사이에서 항목을 끌어서 놓을 수 있도록 합니다. 다음 단계를 수행합니다.

    1. 편집기 `IDropTarget` 에서를 구현 하 여 편집기가 놓기 대상 임을 IDE에 알립니다.

    2. 편집기에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> **도구 상자의**항목을 사용 하거나 사용 하지 않도록 설정 하려면 뷰에서 인터페이스를 구현 합니다.

    3. 서비스에서를 구현 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> 고를 호출 `QueryService` 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 및 인터페이스에 대 한 포인터를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> .

         이러한 단계를 통해 VSPackage가 **도구 상자**에 새 항목을 추가할 수 있습니다.

10. 편집기에 대 한 다른 선택적 기능을 사용할지 여부를 결정 합니다.

    - 편집기에서 찾기 및 바꾸기 명령을 지원 하도록 하려면를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> 합니다.

    - 편집기에서 문서 개요 도구 창을 사용 하려면를 구현 `IVsDocOutlineProvider` 합니다.

    - 편집기에서 상태 표시줄을 사용 하려면를 구현 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 고를 호출 하 여에 `QueryService` 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 포인터를 가져옵니다 `IVsStatusBar` .

         예를 들어 편집기에서 줄/열 정보, 선택 모드 (스트림/상자) 및 삽입 모드 (insert/겹쳐쓰기)를 표시할 수 있습니다.

    - 편집기에서 명령을 지원 하도록 하려면 `Undo` OLE 실행 취소 관리자 모델을 사용 하는 것이 좋습니다. 또는 편집기에서 명령을 직접 처리 하도록 할 수도 있습니다 `Undo` .

11. VSPackage, 메뉴, 편집기 및 기타 기능에 대 한 Guid를 포함 하 여 레지스트리 정보를 만듭니다.

     다음은 편집기를 올바르게 등록 하는 방법을 보여 주기 위해 *.rgs* 파일 스크립트에 배치 하는 코드의 일반적인 예입니다.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. 상황에 맞는 도움말 지원을 구현 합니다.

     이 단계에서는 편집기의 항목에 대 한 F1 도움말 및 동적 도움말 창 지원을 제공할 수 있습니다. 자세한 내용은 [방법: 편집기에 대 한 컨텍스트 제공](../vs-2015/extensibility/how-to-provide-context-for-editors.md?view=vs-2015&preserve-view=true)을 참조 하세요.

13. 인터페이스를 구현 하 여 편집기에서 자동화 개체 모델을 노출 `IDispatch` 합니다.

     자세한 내용은 [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md)을 참조하세요.

## <a name="robust-programming"></a>강력한 프로그래밍

- 편집기 인스턴스는 IDE에서 메서드를 호출할 때 생성 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . 편집기에서 여러 뷰를 지 원하는 경우는 `CreateEditorInstance` 문서 데이터와 문서 뷰 개체를 모두 만듭니다. 문서 데이터 개체가 이미 열려 있는 경우 null `punkDocDataExisting` 이 아닌 값이에 전달 됩니다 `IVsEditorFactory::CreateEditorInstance` . 편집기 팩터리 구현에서는 기존 문서 데이터 개체가 적절 한 인터페이스를 쿼리하여 호환 되는지 여부를 확인 해야 합니다. 자세한 내용은 [다중 문서 뷰 지원](../extensibility/supporting-multiple-document-views.md)을 참조 하세요.

- 단순화 된 포함 방법을 사용 하는 경우 인터페이스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 합니다.

- 내부 활성화를 사용 하기로 결정 한 경우 다음 인터페이스를 구현 합니다.

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > `IOleInPlaceComponent`인터페이스는 OLE 2 메뉴 병합을 방지 하는 데 사용 됩니다.

   `IOleCommandTarget`구현에서는 **잘라내기**, **복사**및 **붙여넣기**와 같은 명령을 처리 합니다. 을 구현 하는 경우 편집기에서 자체의 `IOleCommandTarget` 명령 메뉴 구조를 정의 하거나에서 정의한 표준 명령을 구현할 수 있는지 여부를 결정 *합니다.* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 일반적으로 편집기는 IDE의 메뉴를 사용 및 확장 하 고 자체 도구 모음을 정의 합니다. 그러나 편집기에서 IDE의 표준 명령 집합을 사용 하는 것 외에 고유한 특정 명령을 정의 해야 하는 경우가 종종 있습니다. 편집기에서 사용 하는 표준 명령을 선언 하 고 *vsct* 파일에 새 명령, 상황에 맞는 메뉴, 최상위 메뉴 및 도구 모음을 정의 해야 합니다. 내부 활성화 편집기를 만드는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> OLE 2 메뉴 병합을 사용 하는 대신 *vsct* 파일에서 편집기의 메뉴 및 도구 모음을 구현 하 고 정의 합니다.

- UI에서 메뉴 명령을 crowding 하지 않으려면 새 명령을 고안 전에 IDE에서 기존 명령을 사용 해야 합니다. 공유 명령은 *Sharedcmddef. vsct* 및 *shellcmddef vsct*에 정의 되어 있습니다. 이러한 파일은 기본적으로 설치의 VisualStudioIntegration\Common\Inc 하위 디렉터리에 설치 됩니다 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] .

- `ISelectionContainer` 단일 및 다중 선택을 나타낼 수 있습니다. 선택한 각 개체는 개체로 구현 됩니다 `IDispatch` .

- IDE는 `IOleUndoManager` <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 또는에서 인스턴스화할 수 있는 개체로 액세스할 수 있는 서비스로을 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . 편집기는 `IOleUndoUnit` 각 작업에 대 한 인터페이스를 구현 `Undo` 합니다.

- 사용자 지정 편집기에서 자동화 개체를 노출할 수 있는 두 가지 위치가 있습니다.

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>참고 항목

- [자동화 모델에 기여](../extensibility/internals/contributing-to-the-automation-model.md)