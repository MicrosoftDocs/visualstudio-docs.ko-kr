---
title: 프로젝트 컨텍스트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706593"
---
# <a name="project-context"></a>프로젝트 컨텍스트
사용자가 프로젝트 및 프로젝트 항목을 추가하거나 작업할 때 IDE는 프로젝트 컨텍스트 개념을 사용하여 다양한 작업을 수행하는 방법을 결정합니다.

 일반적으로 파일은 사용자가 새 프로젝트 명령을 선택하여 명시적으로 생성하거나 **파일** 메뉴에서 **프로젝트 열기** 명령을 선택하여 사용할 수 있는 표준 **프로젝트** 개체입니다. 이러한 경우 파일은 프로젝트의 컨텍스트에서 만들어지고 열리며 프로젝트 유형은 문서 편집컨텍스트를 정의합니다.

 일부 프로젝트는 매우 풍부한 컨텍스트를 제공합니다. 예를 들어, 프로젝트는 데이터 바인딩을 위해 프로젝트 범위, 프로그래밍 방식네임 또는 프로젝트 범위 데이터베이스 연결을 관리합니다. 사용자는 솔루션 탐색기에 표시된 프로젝트 항목과 같은 특정 프로젝트 개체를 사용하여 파일 또는 데이터베이스 연결을 직접 자주 열 수 있습니다.

 다른 시간에는 항목의 프로젝트 컨텍스트가 명시적으로 지정되지 않습니다. 예를 들어 사용자가 **파일** 메뉴에서 **기존 파일 열기** 명령을 선택하거나, 디버거가 파일에서 작동하거나, 사용자가 **대화** 상자에서 **파일 찾기** 명령을 클릭할 때 항목의 컨텍스트를 사용할 수 없습니다. 이러한 상황을 처리하기 위해 IDE는 문서를 여는 데 가장 적합한 프로젝트를 찾는 프로세스를 관리하도록 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>

## <a name="see-also"></a>참조
- [프로젝트 우선 순위](../../extensibility/internals/project-priority.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
