---
title: 새 항목 추가 대화 상자에 항목 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710220"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 항목 추가
**새 항목 추가** 대화 상자에 항목을 추가 하는 프로세스는 레지스트리 키로 시작 합니다. 다음 레지스트리 항목에 표시 된 것 처럼 **Additemtemplates** 섹션에는 **새 항목 추가** 대화 상자에서 사용할 수 있는 항목이 배치 된 디렉터리의 경로와 이름이 포함 되어 있습니다.

> [!NOTE]
> 코드 세그먼트 바로 다음에 나오는 테이블에는 레지스트리 항목에 대 한 추가 정보가 포함 되어 있습니다.

 이 섹션은 **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\14.0exp\projects**아래에 있습니다.

 첫 번째 GUID는이 형식의 프로젝트에 대 한 CLSID입니다. 두 번째 GUID는 항목 추가 템플릿에 대해 등록 된 프로젝트 형식을 나타냅니다.

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\ AddItemTemplates 템플릿 \\ \\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \\ 1**

 **@** = #6

 **템플릿**  =  \\ 디렉터리 &lt; Visual Studio SDK 설치 경로 &gt; \\ vsintegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; SomeProject &gt; \\ &lt; SomeProjectItems&gt;

 **Sortpriority** = dword: 00000064

| Name | 유형 | 데이터 ( *.rgs* 파일) | 설명 |
|------------------|-----------| - | - |
| @ (기본값) | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY% | **항목 템플릿 추가** 의 리소스 ID입니다. |
| Val 템플릿 디렉터리 | REG_SZ | % TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | **새 항목 추가** 마법사의 대화 상자에 표시 되는 프로젝트 항목의 경로입니다. |
| Val SortPriority | REG_DWORD | 100 ( [!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)] ) | **새 항목 추가** 대화 상자에 표시 되는 파일의 트리 노드에서 정렬 순서를 결정 합니다. |

> [!NOTE]
> Visual c # 및 Visual Basic 프로젝트 형식에 대 한 GUID는 다음과 같습니다.
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 [ **새 항목 추가** ] 대화 상자 트리의 왼쪽에 있는 노드는 " *% TEMPLATE_PATH% \\ &lt; SomeProjectItems &gt; (으*)로 설정 된 **템플릿**디렉터리에 대해 나열 된 디렉터리입니다. 트리의 추가 요소는 해당 루트 디렉터리 내의 하위 디렉터리를 기반으로 합니다. 프로젝트에 추가할 수 있는 파일은 **새 항목 추가** 대화 상자의 오른쪽 창에 있는 항목입니다.

 일반적으로이 폴더에는 프로젝트에 대 한 템플릿 파일 (예: 템플릿 HTML 또는 *.cpp* 파일)과 마법사 시작을 위한 모든 *.vsz* 파일이 포함 됩니다. 항목을 표시 하는 방법을 제어 하기 위해 디렉터리 이름 및 아이콘 지역화를 위한 .vsdir 파일도 포함할 수 있습니다 *.* 지역화 된 문자열은 **새 항목 추가** 대화 상자 트리에서이 노드를 나타내는 대화 상자에 표시 되는 캡션입니다.

 그러나 하나의 *.vsdir* 파일에 모든 항목이 있을 필요는 없습니다. 디렉터리의 모든 항목에 대해 *.vsdir* 파일 하나를 사용할 수 있습니다. 자세한 내용은 [마법사 (.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md) 및 [템플릿 디렉터리 설명 (.vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)을 참조 하세요.

> [!NOTE]
> 템플릿 디렉터리의 *.vsdir* 파일은 선택 사항입니다. 프로젝트 요소를 디렉터리에 배치 하 고 **새 항목 추가** 대화 상자에 표시 하려는 경우에는 해당 파일을 templates **dir** 문에 지정 된 템플릿 디렉터리에 배치할 수 있습니다. 그러면 해당 프로젝트에 대 한 **새 항목 추가** 대화 상자의 오른쪽 창에 파일이 표시 됩니다. 그러나 파일 또는 아이콘에 대해 지역화 된 캡션을 표시 하려면 templates 디렉터리에 하나 이상의 *.vsdir* 파일을 포함 해야 합니다.

## <a name="group-project-items"></a>프로젝트 항목 그룹화
 **새 항목 추가** 대화 상자 트리의 폴더에 템플릿 그룹을 포함 하려는 경우 루트 템플릿 디렉터리 아래에 항목을 포함 하는 하위 디렉터리가 있어야 합니다. **새 항목 추가** 대화 상자가 사용자에 게 표시 되 면 하위 폴더도 표시 되 고 해당 하위 폴더에서 프로젝트 요소를 선택할 수 있습니다.

 코드 세그먼트의 정렬 우선 순위는 트리 노드의 다른 요소를 기준으로 트리에서이 템플릿 디렉터리가 생성 되는 위치를 결정 합니다. **새 항목 추가** 대화 상자의 경우 대화 상자에서 올바른 위치에 항목이 표시 되도록 정렬 우선 순위를 포함 해야 합니다.

 인터페이스를 구현 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> **새 항목 추가** 대화 상자에 표시 되는 항목을 필터링 할 수도 있습니다. 이 인터페이스를 구현 하면 50 템플릿 및 마법사 파일과 같이를 포함 하는 디스크에 하나의 템플릿 디렉터리를 설정할 수 있습니다. 이러한 방식으로 한 프로젝트 형식에 속하는 20 개의 파일, 다른 프로젝트 형식에 속하는 다른 30 개 파일 및 일반 형식의 프로젝트에서 사용할 수 있는 모든 파일을 사용 하 여 다양 한 프로젝트 형식을 사용할 수 있습니다. 이러한 방식으로 만든 프로젝트 템플릿에 따라 다른 템플릿 파일 집합을 표시할 수 있습니다.

 예를 들어 Visual Basic 프로젝트에서 웹 프로젝트와 클라이언트 프로젝트를 사용할 수 있습니다. 웹 폼은 클라이언트 프로젝트에 추가 하는 데 유용한 항목이 아닙니다. windows forms는 웹 서버 프로젝트에 추가 하는 데 유용한 항목이 아닙니다. 따라서 두 형식의 프로젝트 모두에 대 한 모든 파일을 포함 하는 하나의 템플릿 디렉터리를 만들 수 있습니다. 그런 다음를 구현 하 여 프로젝트의 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 또는 프로젝트 설정 형식에 따라 표시 되지 않아야 하는 항목을 숨길 수 있습니다.

## <a name="filter-project-items"></a>프로젝트 항목 필터링
 `IVsFilterAddProjectItemDlg2` 는 다음과 같은 방법으로 트리 (왼쪽 창) 및 프로젝트 파일 (오른쪽 창)에서 요소를 필터링 하는 데 제공 됩니다.

- 에서 제공 하는 지역화 된 이름 ( *.vsdir* 파일에 포함 된 대화 상자에 표시 되는 캡션)을 기준으로 `IVsFilterAddProjectItemDlg` 합니다.

- 에서 제공 하는 디스크에 있는 파일 및 폴더의 실제 이름 (지역화 되지 않은- *.vsdir* 파일) `IVsFilterAddProjectItemDlg`

- 범주별로 제공 `IVsFilterAddProjectItemDlg2` 됩니다.

  범주별로 필터링 하려면 *웹 폼* 또는 Visual Basic의 *클라이언트 항목과* 같은 *.vsdir* 파일의 항목에 범주 문자열을 제공 합니다. 그런 다음 대화 상자 코드는 *.vsdir* 파일에서 범주 분류를 검색 하 고 사용자에 게 전달 합니다. 그런 다음 해당 정보를의 구현에 전달 하 여 `IVsFilterAddProjectItemDlg2` **새 항목 추가** 대화 상자를 범주별로 필터링 할 수 있습니다. 웹 페이지 또는 클라이언트 Win32 응용 프로그램 사례로 항목을 필터링 할 수도 있습니다. 또한 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 태그가 지정 된 항목을 Microsoft Foundation Classes (MFC) 또는 ATL (active template library) 항목으로 식별할 수 있습니다. 이러한 항목을 식별 하면 프로젝트 시스템에서 범주 및 분류에 따라 시스템을 필터링 할 수 있도록 자체 분류를 정의할 수 있습니다.

  이 필터 기능을 구현 하는 경우 숨겨야 하는 모든 항목의 테이블을 매핑할 필요가 없습니다. 항목을 형식으로 분류 하 고 해당 분류를 *.vsdir* 파일이 나 파일에 배치할 수 있습니다. 그런 다음 인터페이스를 구현 하 여 특정 분류가 포함 된 항목을 숨길 수 있습니다. 이러한 방식으로 프로젝트 내의 상태를 기준으로 **새 항목 추가** 대화 상자에서 항목을 동적으로 만들 수 있습니다.

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [일반적으로 프로젝트를 확장 하는 데 사용 되는 개체에 대 한 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [템플릿 디렉터리 설명 (.vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [마법사 (.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
