---
title: T4 텍스트 변환 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654959"
---
# <a name="customizing-t4-text-transformation"></a>T4 텍스트 변환 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 템플릿은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 변환 프로세스를 통해 프로그램 코드나 다른 텍스트 파일을 생성할 수 있도록 하는의 기능입니다. 를 사용 하 여 [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)] 텍스트 템플릿 지시문 프로세서 또는 텍스트 템플릿 호스트를 사용자 지정 하 여 기본 템플릿 변환 프로세스를 확장할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
 [텍스트 템플릿 변환 프로세스](../modeling/the-text-template-transformation-process.md) 텍스트 변환의 작동 방식에 대해 설명 하 고 템플릿 호스트 및 지시문 프로세서의 역할에 대해 설명 합니다.

 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기](../modeling/creating-custom-t4-text-template-directive-processors.md) 지시문 프로세서는 템플릿을 컴파일하는 동안 실행 되는 것과 같이 템플릿의 지시문을 처리 `<#@template#>.` 하며 어셈블리 및 기타 리소스를 로드할 수 있습니다. 런타임에 리소스를 로드 하는 코드를 삽입할 수도 있습니다. 사용자 고유의 지시문 프로세서를 정의 하 여 템플릿의 복잡성을 줄일 수 있습니다.

 [VS 확장에서 텍스트 변환 호출](../modeling/invoking-text-transformation-in-a-vs-extension.md) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 메뉴 명령이 나 이벤트 처리기와 같은 확장을 작성 하는 경우 확장에서 텍스트 템플릿 서비스를 사용 하 여 텍스트 템플릿을 변환할 수 있습니다. Session 개체를 사용 하 여 매개 변수 데이터를 템플릿에 전달 하 고 지시문을 사용 하 여 템플릿 내에서 값을 가져올 수 있습니다 `<#@parameter#>` .

 [사용자 지정 호스트를 사용 하 여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md) 텍스트 템플릿의 코드가 실행 되 면 호스트는 외부 파일 및 응용 프로그램의 상태에 대 한 액세스를 제공 합니다. 예를 들어에서 텍스트 변환을 실행 하는 호스트는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션 탐색기에 대 한 액세스를 제공할 수 있습니다. 오류 메시지 창에 오류도 표시 됩니다. 다른 컨텍스트에서 텍스트 변환을 실행 하려는 경우 해당 컨텍스트에서 사용할 수 있는 서비스에 대 한 액세스를 제공 하는 고유한 호스트를 정의할 수 있습니다.

 확장을 작성 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 고유 호스트를 작성 하는 대신 기존 텍스트 변환 서비스를 사용 하는 것이 좋습니다. 자세한 내용은 [VS 확장에서 텍스트 변환 호출](../modeling/invoking-text-transformation-in-a-vs-extension.md)을 참조 하세요.

## <a name="reference"></a>참조
 [T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)

 텍스트 템플릿 지시문 및 제어 블록의 구문을 제공 합니다.
