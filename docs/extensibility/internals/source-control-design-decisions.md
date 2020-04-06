---
title: 소스 제어 설계 결정 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705249"
---
# <a name="source-control-design-decisions"></a>소스 제어 디자인 결정
소스 제어를 구현할 때 프로젝트에 대해 다음 디자인 결정을 고려해야 합니다.

## <a name="will-information-be-shared-or-private"></a>정보가 공유되거나 비공개인가요?
 가장 중요한 디자인 결정은 어떤 정보를 검색할 수 있고 비공개인지입니다. 예를 들어 프로젝트의 파일 목록은 공유되지만 이 파일 목록 내에서 일부 사용자는 개인 파일을 갖고 싶어할 수 있습니다. 컴파일러 설정은 공유되지만 시작 프로젝트는 일반적으로 비공개입니다. 설정은 순수하게 공유되거나 재정의와 공유되거나 비공개로 유지됩니다. 의도적으로 솔루션 사용자 옵션(.suo) 파일과 같은 개인 항목은 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]에 체크 인되지 않습니다. .suo 파일과 같은 개인 파일이나 사용자가 만든 특정 개인 파일(예: Visual C#용 .csproj.user 파일 또는 Visual Basic용 .vbproj.user 파일)에 개인 정보를 저장해야 합니다.

 이 결정은 올 인클루시브가 아니며 항목별로 할 수 있습니다.

## <a name="will-the-project-include-special-files"></a>프로젝트에 특수 파일이 포함합니까?
 또 다른 중요한 설계 결정은 프로젝트 구조에서 특수 파일을 사용하는지 여부입니다. 특수 파일은 솔루션 탐색기 및 체크 인 및 체크 아웃 대화 상자에 표시되는 파일의 기반이 되는 숨겨진 파일입니다. 특수 파일을 사용하는 경우 다음 지침을 따르십시오.

1. 특수 파일을 프로젝트 루트 노드(즉, 프로젝트 파일 자체와 연결하지 마십시오)와 연결하지 마십시오. 프로젝트 파일은 단일 파일이어야 합니다.

2. 프로젝트에서 특수 파일을 추가, 제거 또는 이름이 바뀌면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 파일이 특수 파일임을 나타내는 플래그 집합을 통해 적절한 이벤트를 발생시켜야 합니다. 이러한 이벤트는 적절한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 메서드를 호출하는 프로젝트에 대한 응답으로 환경에서 호출됩니다.

3. 프로젝트 또는 편집기에서 파일을 호출하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 해당 파일과 연결된 특수 파일이 자동으로 체크 아웃되지 않습니다. 부모 파일과 함께 특수 파일을 전달합니다. 환경은 전달되는 모든 파일 간의 관계를 감지하고 체크 아웃 UI에서 특수 파일을 적절히 숨깁니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
