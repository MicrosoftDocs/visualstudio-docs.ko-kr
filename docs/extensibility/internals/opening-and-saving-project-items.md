---
title: 프로젝트 항목 열기 및 저장 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706962"
---
# <a name="opening-and-saving-project-items"></a>프로젝트 항목 열기 및 저장
새 프로젝트 형식을 추가 하는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (통합 개발 환경)에서 프로젝트 파일을 열고 저장 하는 과정을 관리 해야 합니다. 다음 항목에서는 파일을 열고 저장 하는 다양 한 방법에 대해 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
- [파일 열기 명령을 사용하여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 IDE에서 **파일 열기** 명령과이 명령에 응답 하는 프로젝트의 역할을 처리 하는 방법에 대 한 단계별 설명을 제공 합니다.

- [연결 프로그램 명령을 사용하여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 IDE에서 **열기** 명령을 처리 하는 방법에 대 한 자세한 단계별 설명을 제공 하 여 표준 편집기를 선택 하는 파일을 여는 메시지를 표시 합니다.

- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)

 프로젝트별 편집기를 사용 하 여 프로젝트에서 특정 형식의 파일을 열도록 지정 하는 방법에 대 한 단계별 지침을 제공 합니다.

- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)

 IDE를 사용 하 여 프로젝트 형식에서 파일의 표준 편집기를 여는 방법을 지정 하는 방법에 대 한 단계별 지침을 제공 합니다.

- [방법: 열린 문서에 대한 편집기 열기](../../extensibility/how-to-open-editors-for-open-documents.md)

 열려 있는 파일에 대 한 프로젝트별 편집기를 여는 방법에 대 한 단계별 지침을 제공 합니다.

- [표준 문서 저장](../../extensibility/internals/saving-a-standard-document.md)

 표준 편집기에서 열린 문서에 대 한 **저장**, 다른 **이름으로**저장, 저장 명령을 **모두** 처리 하는 방법에 대 한 자세한 설명을 제공 합니다.

- [사용자 지정 문서 저장](../../extensibility/internals/saving-a-custom-document.md)

 사용자 지정 편집기에서 열린 문서에 대 한 **저장**, 다른 **이름으로** **저장 및 저장 명령을 처리** 하는 방법에 대 한 다이어그램 및 자세한 설명을 제공 합니다.

- [프로젝트에서 파일을 여는 편집기 결정](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 IDE에서 파일에 적합 한 편집기나 디자이너를 선택 하는 데 따르는 프로세스에 대해 설명 합니다.

## <a name="related-sections"></a>관련 섹션
- [사용자 지정 편집기 및 디자이너 만들기](../../extensibility/creating-custom-editors-and-designers.md)

 IDE에서 호스팅할 수 있는 네 가지 유형의 편집기를 나열 하 고 각 편집기에 대 한 설명을 제공 합니다.

- [프로젝트 형식](../../extensibility/internals/project-types.md):

 프로젝트에서 코드를 컴파일하고 빌드하는 방법, 편집기를 여는 방법 및 프로젝트 항목의 형식을 지정 하는 방법을 설명 합니다.
