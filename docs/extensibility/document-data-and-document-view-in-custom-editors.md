---
title: 사용자 지정 편집기의 문서 데이터 및 문서 보기 | Microsoft Docs
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
ms.openlocfilehash: 608396c79816606b855d49776390b0b1bf9044d7
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012466"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>사용자 지정 편집기의 문서 데이터 및 문서 보기
사용자 지정 편집기는 문서 데이터 개체와 문서 뷰 개체의 두 부분으로 구성 됩니다. 이름에서 알 수 있듯이 document data 개체는 표시 될 텍스트 데이터를 나타냅니다. 마찬가지로 문서 보기 개체 (또는 "보기")는 문서 데이터 개체를 표시할 하나 이상의 창을 나타냅니다.

## <a name="document-data-object"></a>문서 데이터 개체
 문서 데이터 개체는 텍스트 버퍼의 텍스트에 대 한 데이터 표현입니다. 문서 텍스트 및 기타 정보를 저장 하는 COM 개체입니다. 문서 데이터 개체는 또한 문서 지 속성을 처리 하 고 해당 데이터의 여러 뷰를 사용 하도록 설정 합니다. 자세한 내용은 다음을 참조하세요.

 <xref:EnvDTE80.Window2.DocumentData%2A>및 [문서 창](../extensibility/internals/document-windows.md)

 사용자 지정 편집기 및 디자이너는 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 개체 또는 고유한 사용자 지정 버퍼를 사용 하도록 선택할 수 있습니다. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 는 표준 편집기에 대 한 단순화 된 포함 모델을 따르고 여러 뷰를 지원 하며 여러 뷰를 관리 하는 데 사용 되는 이벤트 인터페이스를 제공 합니다.

## <a name="document-view-object"></a>문서 보기 개체
 코드와 기타 텍스트를 표시 하는 창을 문서 보기 또는 보기 라고 합니다. 편집기를 만들 때 단일 창에 텍스트가 표시 되는 단일 보기를 선택할 수 있습니다. 또는 여러 창에서 텍스트를 표시 하는 여러 뷰를 선택할 수 있습니다. 사용자의 선택은 응용 프로그램에 따라 달라 집니다. 예를 들어 side-by-side 편집이 필요한 경우 여러 뷰를 선택할 수 있습니다. 각 보기는 통합 개발 환경 (IDE) 실행 문서 테이블 (RDT)의 항목과 연결 됩니다. 보기 창이 프로젝트 또는 개체에 속합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .

 편집기에서 문서 데이터 개체의 여러 뷰를 지 원하는 경우 문서 데이터와 문서 뷰 개체는 분리 해야 합니다. 그렇지 않으면 함께 그룹화 할 수 있습니다. 자세한 내용은 [다중 문서 뷰 지원](../extensibility/supporting-multiple-document-views.md)을 참조 하세요.

 IDE는 실행 중인 문서 테이블의 각 항목에 대해 ItemID (항목 식별자)를 일치 시켜 문서를 포함 하는 솔루션이 닫혀 있는 경우와 같은 이벤트에 대 한 뷰에 알림을 보냅니다. 이에 대 한 자세한 내용은 [문서 테이블 실행](../extensibility/internals/running-document-table.md)을 참조 하세요.

 사용자 지정 편집기에 대 한 보기를 만드는 두 가지 옵션이 있습니다. 하나는 ActiveX 컨트롤이 나 문서 데이터 개체를 사용 하 여 창에서 뷰를 호스트 하는 내부 활성화 모델입니다. 두 번째는 뷰가에서 호스팅되고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 창 명령을 처리 하도록 구현 되는 단순화 된 포함 모델입니다. 내부 활성화 모델에 대 한 자세한 내용은 [내부 활성화](../vs-2015/misc/in-place-activation.md?view=vs-2015)를 참조 하십시오. 단순화 된 포함 모델에 대 한 자세한 내용은 [간소화 된 포함](../extensibility/simplified-embedding.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [다중 문서 뷰 지원](../extensibility/supporting-multiple-document-views.md)
- [단순화 포함](../extensibility/simplified-embedding.md)
- [방법: 문서 데이터에 보기 연결](../extensibility/how-to-attach-views-to-document-data.md)
- [문서 잠금 보유자 관리](../extensibility/document-lock-holder-management.md)
- [단일 및 다중 탭 뷰](../extensibility/single-and-multi-tab-views.md)
- [표준 문서 저장](../extensibility/internals/saving-a-standard-document.md)
- [지 속성 및 실행 중인 문서 테이블](../extensibility/internals/persistence-and-the-running-document-table.md)
- [프로젝트에서 파일을 여는 편집기 결정](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)