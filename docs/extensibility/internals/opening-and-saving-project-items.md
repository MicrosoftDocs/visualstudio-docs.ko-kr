---
title: 프로젝트 아이템 열기 및 저장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706962"
---
# <a name="opening-and-saving-project-items"></a>프로젝트 항목 열기 및 저장
새 프로젝트 유형을 추가할 때 통합 개발 환경(IDE)에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 파일의 열기 및 저장을 관리해야 합니다. 다음 항목에서는 파일을 열고 저장하는 다양한 방법에 대해 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [파일 열기 명령을 사용하여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 IDE가 **파일 열기** 명령을 처리하는 방법과 이 명령에 응답하는 프로젝트의 역할에 대한 단계별 설명을 제공합니다.

- [연결 프로그램 명령을 사용하여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 IDE가 **열기** 명령을 처리하는 방법에 대한 자세한 단계별 설명을 제공하여 표준 편집기 중 몇 가지 선택 항목이 있는 파일을 열도록 합니다.

- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)

 프로젝트 별 편집기에서 프로젝트에서 특정 형식의 파일을 열어야 하는지 지정하기 위한 단계별 지침을 제공합니다.

- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)

 IDE가 프로젝트 유형의 파일에 대한 표준 편집기를 열 수 있도록 하는 방법을 지정하기 위한 단계별 지침을 제공합니다.

- [방법: 열린 문서에 대한 편집기 열기](../../extensibility/how-to-open-editors-for-open-documents.md)

 열려 있는 파일에 대 한 프로젝트 별 편집기를 여는 단계별 지침을 제공합니다.

- [표준 문서 저장](../../extensibility/internals/saving-a-standard-document.md)

 표준 편집기에서 열린 문서에 대한 **저장,** **현재 저장**및 **저장 명령에** 대해 IDE가 처리하는 방법에 대한 자세한 설명을 제공합니다.

- [사용자 지정 문서 저장](../../extensibility/internals/saving-a-custom-document.md)

 사용자 지정 편집기에서 열린 문서에 대한 **저장,** **현재 저장**및 **저장 명령에** 대해 IDE가 처리하는 방법에 대한 다이어그램 및 자세한 설명을 제공합니다.

- [프로젝트에서 파일을 여는 편집기 결정](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 IDE가 파일에 적합한 편집기 또는 디자이너를 선택하는 프로세스에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
- [사용자 지정 편집기 및 디자이너 만들기](../../extensibility/creating-custom-editors-and-designers.md)

 IDE에서 호스팅할 수 있는 네 가지 유형의 편집기와 각 편집기의 설명을 나열합니다.

- [프로젝트 유형](../../extensibility/internals/project-types.md)

 프로젝트가 코드를 컴파일하고 빌드하는 방법, 편집기 의 열기 방법 및 프로젝트 항목의 서식을 지정하는 방법을 제어하는 방법에 대해 설명합니다.
