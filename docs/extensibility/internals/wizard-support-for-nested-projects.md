---
title: 중첩 된 프로젝트에 대한 마법사 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703200"
---
# <a name="wizard-support-for-nested-projects"></a>중첩된 프로젝트에 대한 마법사 지원
IDE는 중첩된 프로젝트의 상위 프로젝트에서 구현할 수 있는 새 **프로젝트** 마법사와 **항목 추가** 마법사의 두 마법사를 실행합니다.

 사용자가 **프로젝트 추가를** 선택하고 파일 메뉴에서 **새 프로젝트** **추가를** 클릭하거나 솔루션 탐색기에서 **새 프로젝트** 추가 및 마우스 오른쪽 단추를 클릭하여 **새 프로젝트** 마법사를 시작하면 IDE는 AddProject 명령을 실행하고 부모 프로젝트의 **AddProject** 명령 구현은 템플릿 프로젝트 파일을 반환하거나 컨텍스트 매개 변수 집합이 있는 마법사(.vsz) 파일을 사용합니다. **AddProject**

 마찬가지로 부모 프로젝트의 **AddItem** 마법사 구현은 컨텍스트 매개 변수집합이 다른 .vsz 파일을 반환합니다.

 마법사에 대한 자세한 내용은 [마법사(를 참조하십시오. Vsz) 파일,](../../extensibility/internals/wizard-dot-vsz-file.md) [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md) 및 프로젝트 및 항목 템플릿 [등록](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
