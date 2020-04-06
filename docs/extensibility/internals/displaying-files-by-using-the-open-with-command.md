---
title: 명령으로 열기를 사용하여 파일 표시 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708587"
---
# <a name="display-files-by-using-the-open-with-command"></a>열기 명령을 사용하여 파일 표시
프로젝트는 IDE에 대화 상자 **열기를** 표시하도록 요청할 수 있습니다. 이 요청은 사용자가 표준 편집기를 선택한 파일을 열라는 메시지를 표시합니다. 다음 단계에서는 이 프로세스를 설명합니다.

1. 프로젝트는 매개 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>변수에 `OSE_UseOpenWithDialog` 대한 값을 `OSEOpenDocEditor` 지정하는 것을 호출합니다.

2. 문서의 파일 이름 확장명에 따라 IDE는 레지스트리에 나열된 편집자가 지정된 문서를 열 수 있는지 결정하고 이 정보를 **대화** 상자열기 상자에 표시합니다.

    > [!NOTE]
    > **열기** 대화 상자에 포함해야 하는 내장 편집기가 있는 프로젝트는 이러한 각 편집기의 편집기 팩터리를 등록해야 합니다. 본질적인 편집기는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드의 구현에 적용되는 특정 유형의 프로젝트와 함께만 작동합니다. IDE에는 핵심 텍스트 편집기와 바이너리 편집기용 에디터 팩터리가 내장되어 있습니다. 또한 IDE는 등록된 각 Windows 파일 연결을 대신하여 편집기 팩터리의 인스턴스를 만듭니다. 이러한 파일의 예는 마이크로 소프트 워드입니다.

3. 사용자가 **열기** 대화 상자에서 항목을 선택하면 IDE는 메서드를 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 문서를 엽니다. 자세한 내용은 [방법: 표준 편집기 열기를](../../extensibility/how-to-open-standard-editors.md)참조하십시오.

## <a name="see-also"></a>참조
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
- [파일 열기 명령을 사용하여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)
