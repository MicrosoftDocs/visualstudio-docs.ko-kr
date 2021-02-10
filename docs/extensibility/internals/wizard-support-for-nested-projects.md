---
title: 중첩 프로젝트에 대 한 마법사 지원 | Microsoft Docs
description: 부모 프로젝트가 Visual Studio SDK에서 VSPackage의 중첩 된 프로젝트에 대해 구현할 수 있는 두 가지 마법사에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f2cd84379ead1cd45296ae370aab215a37cf4b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935873"
---
# <a name="wizard-support-for-nested-projects"></a>중첩된 프로젝트에 대한 마법사 지원
IDE는 중첩 된 프로젝트용 부모 프로젝트에서 구현할 수 있는 두 가지 마법사 인 **새 프로젝트** 마법사와 **항목 추가** 마법사를 실행 합니다.

 사용자가 파일 메뉴에서 **프로젝트 추가** 를 선택 하 **고 새 프로젝트를 클릭 하거나** **추가** 를 선택 하 고 솔루션 탐색기의 **새 프로젝트** 를 마우스 오른쪽 단추로 클릭 하 여 **새 프로젝트** 마법사를 시작 하는 경우, IDE는 **addproject** 명령을 실행 하 고, 부모 프로젝트의 **addproject** 명령 구현은 템플릿 프로젝트 파일 또는 컨텍스트 매개 변수 집합이 있는 마법사 (.vsz) 파일을 반환 합니다.

 마찬가지로, 부모 프로젝트의 **AddItem** 마법사 구현은 다른 컨텍스트 매개 변수 집합을 포함 하는 .vsz 파일을 반환 합니다.

 마법사에 대 한 자세한 내용은 [마법사 (를 참조 하세요. .Vsz 파일](../../extensibility/internals/wizard-dot-vsz-file.md), [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md) 및 [프로젝트 템플릿과 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
