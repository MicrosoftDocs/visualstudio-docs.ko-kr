---
title: 사용자 지정 편집기의 문서 데이터 및 문서 보기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712141"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>사용자 지정 편집기의 문서 데이터 및 문서 보기
사용자 지정 편집기는 문서 데이터 개체와 문서 뷰 개체의 두 부분으로 구성됩니다. 이름에서 볼 수 있듯이 문서 데이터 개체는 표시할 텍스트 데이터를 나타냅니다. 마찬가지로 문서 뷰 개체(또는 "뷰")는 문서 데이터 개체를 표시할 하나 이상의 창을 나타냅니다.

## <a name="document-data-object"></a>문서 데이터 개체
 문서 데이터 개체는 텍스트 버퍼에 있는 텍스트의 데이터 표현입니다. 문서 텍스트 및 기타 정보를 저장하는 COM 개체입니다. 또한 문서 데이터 개체는 문서 지속성을 처리하고 해당 데이터의 여러 보기를 활성화합니다. 자세한 내용은 다음을 참조하세요.

 <xref:EnvDTE80.Window2.DocumentData%2A>및 [문서 윈도우](../extensibility/internals/document-windows.md).

 사용자 지정 편집기 및 디자이너는 개체 또는 자체 사용자 지정 버퍼를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 사용하도록 선택할 수 있습니다. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>표준 편집기의 단순화된 임베딩 모델을 따르고, 여러 뷰를 지원하며, 여러 뷰를 관리하는 데 사용되는 이벤트 인터페이스를 제공합니다.

## <a name="document-view-object"></a>문서 뷰 객체
 코드 및 기타 텍스트를 표시하는 창을 문서 보기 또는 보기라고 합니다. 편집기 작성 할 때 텍스트가 단일 창에 표시되는 단일 보기를 선택할 수 있습니다. 또는 텍스트가 두 개 이상의 창에 표시되는 여러 보기를 선택할 수 있습니다. 선택한 용도는 응용 프로그램에 따라 다릅니다. 예를 들어 나란히 편집해야 하는 경우 여러 뷰를 선택합니다. 각 뷰는 통합 개발 환경(IDE) 실행 문서 테이블(RDT)의 항목과 연결됩니다. 뷰 창은 프로젝트 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 객체에 속합니다.

 편집기에서 문서 데이터 개체의 여러 뷰를 지원하는 경우 문서 데이터와 문서 뷰 개체는 분리되어야 합니다. 그렇지 않으면 함께 그룹화할 수 있습니다. 자세한 내용은 [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)을 참조하십시오.

 IDE는 실행 중인 문서 테이블의 각 항목에 대한 항목 식별자(ItemID)를 일치시켜 이벤트에 대한 보기를(예: 문서가 포함된 솔루션이 닫힌 경우)에 대해 설명합니다. 이에 대한 자세한 내용은 [문서 실행 테이블을](../extensibility/internals/running-document-table.md)참조하십시오.

 사용자 지정 편집기의 뷰를 만드는 데는 두 가지 옵션이 있습니다. 하나는 ActiveX 컨트롤 또는 문서 데이터 개체를 사용하여 창에서 뷰가 호스팅되는 내부 활성화 모델입니다. 두 번째는 단순화된 임베딩 모델로, 뷰가 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 호스트되고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 창 명령을 처리하도록 구현됩니다. 내부 활성화 모델에 대한 자세한 내용은 [내부 활성화](/visualstudio/misc/in-place-activation?view=vs-2015)를 참조하십시오. 단순화된 임베딩 모델에 대한 자세한 내용은 [단순화된 임베딩](../extensibility/simplified-embedding.md)을 참조하십시오.

## <a name="see-also"></a>참조

- [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)
- [단순화된 임베딩](../extensibility/simplified-embedding.md)
- [방법: 뷰를 문서에 첨부하여 데이터를 문서화합니다.](../extensibility/how-to-attach-views-to-document-data.md)
- [문서 잠금 홀더 관리](../extensibility/document-lock-holder-management.md)
- [단일 및 다중 탭 보기](../extensibility/single-and-multi-tab-views.md)
- [표준 문서 저장](../extensibility/internals/saving-a-standard-document.md)
- [지속성 및 실행 중인 문서 테이블](../extensibility/internals/persistence-and-the-running-document-table.md)
- [프로젝트에서 파일을 여는 편집기 결정](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
