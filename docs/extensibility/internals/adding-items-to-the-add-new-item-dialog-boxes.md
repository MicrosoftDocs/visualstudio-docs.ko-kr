---
title: 새 항목 대화 상자 추가에 항목 추가 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710220"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 항목 추가
**새 항목 추가** 대화 상자에 항목을 추가하는 프로세스는 레지스트리 키로 시작합니다. 다음 레지스트리 항목에 표시된 것처럼 **AddItemTemplates** 섹션에는 **새 항목 추가** 대화 상자에서 사용할 수 있는 항목을 넣을 디렉터리 의 경로와 이름이 포함되어 있습니다.

> [!NOTE]
> 코드 세그먼트 바로 다음의 테이블에는 레지스트리 항목에 대한 추가 정보가 포함되어 있습니다.

 이 섹션은 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\프로젝트**아래에 있습니다.

 첫 번째 GUID는 이러한 유형의 프로젝트에 대한 CLSID입니다. 두 번째 GUID는 항목 추가 템플릿에 대해 등록된 프로젝트 유형을 나타냅니다.

 **\\{C061DB26-5833-11D2-96F5-00000000000000} \\추가 항목\\템플릿 템플릿DIR\\{ACEF4EB2-57CF-11D2-96F4-0000000000000}\\1**

 **@**= #6

 **TemplatesDir** = \\&lt;비주얼 스튜디오 SDK\\&lt;설치&gt;\\&lt;경로&gt;\\&gt;\\&lt;VS통합&gt;\\&lt;일부폴더 일부 패키지 일부 프로젝트 일부 프로젝트항목&gt;

 **정렬 우선 순위** = dword:00000064

| 이름 | 형식 | *데이터(.rgs* 파일에서) | 설명 |
|------------------|-----------| - | - |
| @ (기본값) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | **항목 템플릿 추가를** 위한 리소스 ID입니다. |
| 발 템플릿디르 | REG_SZ | %TEMPLATE_PATH%\\&lt;일부 프로젝트항목&gt; | 새 항목 **추가** 마법사에 대한 대화 상자에 표시되는 프로젝트 항목의 경로입니다. |
| 발 정렬 우선 순위 | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]() | **새 항목 추가** 대화 상자에 표시되는 파일의 트리 노드에서 정렬 순서를 결정합니다. |

> [!NOTE]
> 시각적 C# 및 시각적 기본 프로젝트 유형에 대한 GUIDS는 다음과 같습니다.
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 **TemplatesDir에**대해 나열된 디렉터리, *이는\\&lt;%TEMPLATE_PATH% SomeProjectItems는&gt;* **새 항목 추가** 대화 상자 트리의 왼쪽에 있는 노드입니다. 트리의 추가 요소는 해당 루트 디렉터리 내의 하위 디렉터리를 기반으로 합니다. 프로젝트에 추가할 수 있는 파일은 **새 항목 추가** 대화 상자의 오른쪽 창에 있는 항목입니다.

 일반적으로 이 폴더에는 템플릿 HTML 또는 *.cpp* 파일과 같은 프로젝트의 템플릿 파일과 마법사를 시작하기 위한 *.vsz* 파일이 포함됩니다. 항목이 표시되는 방식을 제어하려면 디렉터리 이름과 아이콘을 지역화하기 위한 *.vsdir* 파일을 포함할 수도 있습니다. 지역화된 문자열은 **새 항목 추가** 대화 상자 트리에서 이 노드를 나타내는 대화 상자에 나타나는 캡션입니다.

 그러나 모든 것을 *하나의 .vsdir* 파일에 포함할 필요는 없습니다. 디렉터리내의 모든 항목에 대해 *.vsdir* 파일을 하나씩 가질 수 있습니다. 자세한 내용은 [마법사(.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md) 및 [템플릿 디렉터리 설명(.vsdir) 파일을](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)참조하십시오.

> [!NOTE]
> 템플릿 디렉토리의 *.vsdir* 파일은 선택 사항입니다. 디렉터리에 프로젝트 요소를 배치하고 **새 항목 추가** 대화 상자에 표시하려는 경우 **TemplatesDir** 문에 지정된 템플릿 디렉토리에 해당 파일을 넣을 수 있습니다. 그러면 해당 프로젝트의 **새 항목 추가** 대화 상자의 오른쪽 창에 파일이 표시됩니다. 그러나 파일 또는 아이콘에 대한 지역화된 캡션을 표시하려면 템플릿 디렉토리에 하나 이상의 *.vsdir* 파일을 포함해야 합니다.

## <a name="group-project-items"></a>프로젝트 항목 그룹화
 **새 항목 추가** 대화 상자 트리의 폴더에 템플릿 그룹을 포함하려면 해당 항목이 포함된 루트 템플릿 디렉토리 아래에 하위 디렉토리가 있어야 합니다. 새 **항목 추가** 대화 상자가 사용자에게 표시되면 하위 폴더도 표시되고 해당 항목에서 프로젝트 요소를 선택할 수 있습니다.

 코드 세그먼트의 정렬 우선 순위는 트리 노드의 다른 요소를 기준으로 트리에서 이 템플릿 디렉터리를 만들 위치를 결정합니다. 새 **항목 추가** 대화 상자의 경우 정렬 우선 순위는 항목이 대화 상자의 올바른 위치에 표시되도록 포함해야 합니다.

 새 항목 추가 대화 상자에 표시되는 내용을 필터링하는 인터페이스를 구현할 수도 있습니다. **Add New Item** <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 이 인터페이스를 구현하면 50개의 템플릿 및 마법사 파일과 같은 디스크에 하나의 템플릿 디렉터리를 설정할 수 있습니다. 이렇게 하면 한 프로젝트 유형에 속하는 파일 20개, 다른 프로젝트 유형에 속하는 다른 30개의 파일 및 일반 프로젝트 유형에서 사용할 수 있는 모든 파일이 있는 다양한 프로젝트 형식을 가질 수 있습니다. 이러한 방식으로 작성되는 프로젝트 템플릿에 따라 다른 템플릿 파일 집합을 표시할 수 있습니다.

 예를 들어 Visual Basic 프로젝트에 웹 프로젝트와 클라이언트 프로젝트가 있을 수 있습니다. 웹 양식은 클라이언트 프로젝트에 추가할 수 있는 유용한 항목이 아니며 Windows 양식은 웹 서버 프로젝트에 추가할 수 있는 유용한 항목이 아닙니다. 따라서 두 유형의 프로젝트모두에 대한 모든 파일이 포함된 하나의 템플릿 디렉터리를 만들 수 있습니다. 그런 다음 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>을 구현하여 프로젝트의 프로젝트 또는 프로젝트 설정 유형에 따라 표시되지 않아야 하는 항목을 숨길 수 있습니다.

## <a name="filter-project-items"></a>프로젝트 항목 필터링
 `IVsFilterAddProjectItemDlg2`다음과 같은 방법으로 트리의 요소 필터링(왼쪽 창) 및 프로젝트 파일(오른쪽 창)을 제공합니다.

- 에서 제공하는 `IVsFilterAddProjectItemDlg`지역화된 이름(.vsdir 파일에 포함된 대화 *.vsdir* 상자에 표시되는 캡션)을 참조하십시오.

- `IVsFilterAddProjectItemDlg`에서 제공하는 디스크의 파일 및 폴더의 실제 이름(지역화되지 않은 *.vsdir* 파일 없음)으로

- 범주별, 에서 `IVsFilterAddProjectItemDlg2`제공합니다.

  범주별로 필터링하려면 Visual Basic의 *웹 양식* 또는 *클라이언트* 항목과 같은 *.vsdir* 파일의 항목에 범주 문자열을 제공합니다. 그런 다음 대화 상자 코드는 *.vsdir* 파일에서 범주 분류를 검색하여 전달합니다. 그런 다음 해당 정보를 구현에 `IVsFilterAddProjectItemDlg2` 전달하여 **범주별로 새 항목 추가** 대화 상자를 필터링할 수 있습니다. 웹 페이지 또는 클라이언트 Win32 응용 프로그램 사례로 항목을 필터링할 수도 있습니다. 또한 태그가 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 지정된 항목을 Microsoft 기초 클래스(MFC) 또는 활성 템플릿 라이브러리(ATL) 항목으로 식별할 수 있습니다. 이러한 항목을 식별하면 프로젝트 시스템은 범주 및 분류에 따라 시스템을 필터링할 수 있도록 자체 분류를 정의할 수 있습니다.

  이 필터 기능을 구현하는 경우 숨김해야 하는 모든 항목의 테이블을 매핑할 필요가 없습니다. 항목을 유형으로 분류하고 *.vsdir* 파일 또는 파일에 분류를 넣을 수 있습니다. 그런 다음 인터페이스를 구현하여 특정 분류가 있는 항목을 숨길 수 있습니다. 이렇게 하면 프로젝트 내의 상태에 따라 **새 항목 추가** 대화 상자의 항목을 동적으로 만들 수 있습니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [템플릿 디렉토리 설명(.vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [마법사(.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
