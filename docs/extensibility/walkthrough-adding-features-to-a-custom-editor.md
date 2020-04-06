---
title: '연습: 사용자 지정 편집기에 기능 추가 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697785"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>연습: 사용자 지정 편집기에 피처 추가
사용자 지정 편집기를 만든 후 추가 기능을 추가할 수 있습니다.

## <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage에 대한 편집기를 만들려면

1. Visual Studio 패키지 프로젝트 템플릿을 사용하여 사용자 지정 편집기 만들기

     자세한 내용은 [연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)를 참조하십시오.

2. 편집기에서 단일 보기를 지원할지 아니면 여러 뷰를 지원할지 결정합니다.

     **새 창** 명령을 지원하거나 양식 보기 및 코드 보기가 있는 편집기에는 별도의 문서 데이터 개체와 문서 보기 개체가 필요합니다. 단일 뷰만 지원하는 편집기에서 문서 데이터 개체와 문서 뷰 개체를 동일한 개체에서 구현할 수 있습니다.

     여러 보기의 예는 [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)참조

3. 인터페이스를 설정하여 편집기 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 팩터리를 구현합니다.

     자세한 내용은 [편집기 팩터리를](../extensibility/editor-factories.md)참조하십시오.

4. 편집기에서 내부 활성화를 사용할지 또는 단순화된 임베디드를 사용하여 문서 보기 개체 창을 관리할지 여부를 결정합니다.

     단순화된 임베디지 편집기 창은 표준 문서 보기를 호스트하고 내부 활성화 편집기 창은 ActiveX 컨트롤 또는 기타 활성 개체를 문서 보기로 호스트합니다. 자세한 내용은 [단순화된 임베딩](../extensibility/simplified-embedding.md) 및 [내부 활성화를](/visualstudio/misc/in-place-activation?view=vs-2015)참조하십시오.

5. 명령을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 처리하는 인터페이스를 구현합니다.

6. 외부 파일 변경 에 대한 문서 지속성 및 응답을 제공합니다.

    1. 파일을 유지하려면 편집기의 문서 데이터 개체를 구현합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>

    2. 외부 파일 변경에 응답하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 편집기의 문서 데이터 개체를 구현하고 구현합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>

        > [!NOTE]
        > 에 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> 대한 포인터를 `IVsFileChangeEx`얻으려면 전화합니다.

7. 소스 코드 컨트롤을 통해 문서 편집 이벤트를 조정합니다. 다음 단계를 수행하세요.

    1. 에 호출하여 `IVsQueryEditQuerySave2` `QueryService` 포인터를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>가져옵니다.

    2. 첫 번째 편집 이벤트가 발생하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 메서드를 호출합니다.

         이 메서드는 아직 체크 아웃되지 않은 경우 파일을 체크 아웃하라는 메시지를 표시합니다. 오류를 방지하려면 "체크 아웃되지 않은 파일" 조건을 처리해야 합니다.

    3. 마찬가지로 파일을 저장하기 전에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 메서드를 호출합니다.

         이 메서드는 파일을 저장 하지 않은 경우 또는 마지막 저장 이후 변경 된 경우 파일을 저장 하는 메시지를 표시 합니다.

8. **속성** 창을 사용하여 편집기에서 선택한 텍스트의 속성을 표시합니다. 다음 단계를 수행하세요.

    1. 텍스트 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 선택이 변경될 때마다 호출하여 구현을 전달합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>

    2. 서비스에 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 전화하여 에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>포인터를 얻습니다.

9. 사용자가 편집기와 도구 상자 간에 또는 외부 **편집기(예:** Microsoft Word)와 도구 상자 간에 항목을 드래그 앤 **드롭할**수 있습니다. 다음 단계를 수행하세요.

    1. 편집기를 구현하여 `IDropTarget` 편집기의 삭제 대상이 있음을 IDE에 알립니다.

    2. 편집기에서 도구 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> **상자에서**항목을 활성화 및 비활성화할 수 있도록 뷰에서 인터페이스를 구현합니다.

    3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 하 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 고 및 인터페이스에 대 한 포인터를 얻기 위해 서비스에 호출 합니다.

         이 단계를 수행하면 VSPackage에서 **도구 상자에**새 항목을 추가할 수 있습니다.

10. 편집기의 다른 선택적 기능을 사용할지 여부를 결정합니다.

    - 편집기에서 찾기 및 바꾸기 명령을 지원하려면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>을 구현합니다.

    - 편집기에서 문서 개요 도구 창을 사용하려면 `IVsDocOutlineProvider`을 구현합니다.

    - 편집기에서 상태 표시줄을 사용하려면 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 대한 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 포인터를 얻기 `IVsStatusBar`위해 구현하고 호출합니다.

         예를 들어, 편집기는 라인/컬럼 정보, 선택 모드(스트림/박스) 및 삽입 모드(삽입/오버스트라이크)를 표시할 수 있습니다.

    - 편집기에서 `Undo` 명령을 지원하려면 OLE 취소 관리자 모델을 사용하는 것이 좋습니다. 또는 편집기에서 명령을 직접 처리할 `Undo` 수 있습니다.

11. VSPackage에 대한 GUID, 메뉴, 편집기 및 기타 기능을 포함한 레지스트리 정보를 만듭니다.

     다음은 편집기를 올바르게 등록하는 방법을 보여 주기 위해 *.rgs* 파일 스크립트에 넣을 코드의 일반적인 예입니다.

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

12. 상황에 맞는 도움말 지원을 구현합니다.

     이 단계를 통해 편집기의 항목에 대한 F1 도움말 및 동적 도움말 창 지원을 제공할 수 있습니다. 자세한 내용은 [편집자에 대한 컨텍스트 제공 방법: 을](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015)참조하십시오.

13. 인터페이스를 구현하여 편집기에서 자동화 `IDispatch` 개체 모델을 노출합니다.

     자세한 내용은 [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md)을 참조하세요.

## <a name="robust-programming"></a>강력한 프로그래밍

- 편집기 인스턴스는 IDE가 메서드를 호출할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 때 만들어집니다. 편집기에서 여러 뷰를 지원하는 경우 문서 데이터와 문서 뷰 개체를 모두 `CreateEditorInstance` 만듭니다. 문서 데이터 개체가 이미 열려 있으면 `punkDocDataExisting` null이 아닌 `IVsEditorFactory::CreateEditorInstance`값이 로 전달됩니다. 편집기 팩터리 구현은 해당 문서에 대한 적절한 인터페이스를 쿼리하여 기존 문서 데이터 개체와 호환되는지 여부를 결정해야 합니다. 자세한 내용은 [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)을 참조하십시오.

- 단순화된 임베딩 방법을 사용하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스를 구현합니다.

- 내부 활성화를 사용하기로 결정한 경우 다음 인터페이스를 구현합니다.

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > 인터페이스는 `IOleInPlaceComponent` OLE 2 메뉴 병합을 방지하는 데 사용됩니다.

   `IOleCommandTarget` 구현에서는 **잘라내기,** **복사**및 붙여넣기 와 같은 명령을 **처리합니다.** 구현 `IOleCommandTarget`할 때 편집기자체의 명령 메뉴 구조를 정의하기 위해 *자체 .vsct* 파일이 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]필요한지 또는 에 의해 정의된 표준 명령을 구현할 수 있는지 여부를 결정합니다. 일반적으로 편집자는 IDE의 메뉴를 사용하고 확장하고 자체 도구 모음을 정의합니다. 그러나 편집기는 IDE의 표준 명령 집합을 사용하는 것 외에도 고유한 특정 명령을 정의해야 하는 경우가 많습니다. 편집자는 사용하는 표준 명령을 선언한 다음 *.vsct* 파일에서 새 명령, 컨텍스트 메뉴, 최상위 메뉴 및 도구 모음을 정의해야 합니다. 내부 활성화 편집기만들기의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> OLE 2 메뉴 병합을 사용하는 대신 *.vsct* 파일에서 편집기의 메뉴 및 도구 모음을 구현하고 정의합니다.

- UI에서 메뉴 명령이 혼잡하지 않도록 하려면 새 명령을 발명하기 전에 IDE의 기존 명령을 사용해야 합니다. 공유 명령은 *SharedCmdDef.vsct* 및 *ShellCmdDef.vsct에 정의됩니다.* 이러한 파일은 설치의 VisualStudioIntegration\Common\Inc 하위 디렉토리에 기본적으로 설치됩니다. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]

- `ISelectionContainer`단일 및 다중 선택 항목을 모두 표현할 수 있습니다. 선택한 각 개체는 `IDispatch` 개체로 구현됩니다.

- IDE는 `IOleUndoManager` 에서 액세스할 수 있는 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 서비스또는 를 통해 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>인스턴스화할 수 있는 개체로 구현합니다. 편집기는 `IOleUndoUnit` 각 `Undo` 작업에 대한 인터페이스를 구현합니다.

- 사용자 지정 편집기에서 자동화 개체를 노출할 수 있는 두 가지 방법이 있습니다.

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>참조

- [자동화 모델에 기여](../extensibility/internals/contributing-to-the-automation-model.md)
