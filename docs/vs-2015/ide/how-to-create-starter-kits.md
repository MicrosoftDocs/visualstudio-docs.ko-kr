---
title: '방법: 시작 키트 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Starter Kits, creating
ms.assetid: ed7d1844-7c01-424a-a831-5003efe0f7bc
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f9df8d85c600cd383a9a9059e689e6cb9f232d8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668035"
---
# <a name="how-to-create-starter-kits"></a>방법: 시작 키트 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

시작 키트에는 완전한 애플리케이션에 대한 코드와 애플리케이션을 수정하거나 확장하는 방법에 대한 설명서가 들어 있습니다. 시작 키트를 만드는 것은 근본적으로 일반 프로젝트 템플릿을 만드는 것과 동일합니다. 단, 시작 키트에 기초한 프로젝트가 생성될 때 열리도록 설정된 설명서 파일이 시작 키트에 포함된다는 점이 다릅니다.

## <a name="designing-and-developing-a-starter-kit"></a>시작 키트 디자인 및 개발
 먼저 개발하고 대상 사용자를 정의하려는 시작 키트 유형을 식별해야 합니다. 그런 다음 프로젝트와 설명서를 디자인하여 목표를 달성하십시오.

 간단한 애플리케이션 또는 플러그 인을 만드는 경우

- 오류 없이 빌드되는 프로젝트를 만듭니다.

- 추가 작업을 구현하기 위한 템플릿 코드를 추가합니다(선택 사항).

- 설명서를 준비합니다.

  학습 도구를 만드는 경우

- 오류 없이 빌드되는 프로젝트를 만듭니다.

- 코드 조각 및 항목 템플릿 등의 리소스를 구성합니다.

- 설명서를 준비합니다.

## <a name="creating-a-template"></a>템플릿 만들기
 프로젝트와 설명서를 완료하면 시작 키트용 프로젝트 템플릿을 만들 준비가 된 것입니다. 이 프로세스는 프로젝트 템플릿을 만드는 것과 완전히 동일합니다.

 다음 항목에는 템플릿 만들기에 대한 정보가 포함되어 있습니다.

 [방법: 프로젝트 템플릿 만들기](../ide/how-to-create-project-templates.md) 템플릿 **내보내기** 마법사를 사용 하 여 템플릿을 만드는 방법을 설명 합니다.

 [방법: 기존 템플릿 업데이트](../ide/how-to-update-existing-templates.md) 내보낸 템플릿을 편집 하는 방법을 설명 합니다. 이 절차를 사용하여 .vstemplate 파일을 수정하고 시작 키트를 사용자 지정합니다.

## <a name="see-also"></a>관련 항목
 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md) [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
