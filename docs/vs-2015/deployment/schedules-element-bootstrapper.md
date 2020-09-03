---
title: '&lt;일정 &gt; 요소 (부트스트래퍼) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85ffab2272a55bfe77c5f2a73c6e25967a203c85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206100"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;일정 &gt; 요소 (부트스트래퍼)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요소에는 요소로 `Schedules` `Schedule` 정의 된 명령을 실행 해야 하는 특정 시간을 정의 하는 요소가 포함 되어 있습니다 `Command` .  
  
## <a name="syntax"></a>Syntax  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 요소는 `Schedules` 요소의 자식입니다 `Product` . 각 `Product` 요소에는 요소가 최대 하나만 있을 수 있습니다 `Schedules` . `Schedules` 요소에는 특성이 없습니다.  
  
## <a name="schedule"></a>예약  
 요소는 `Schedule` 요소의 자식입니다 `Schedules` . 요소에는 `Schedules` 요소가 하나 이상 있어야 합니다 `Schedule` .  
  
 `Schedule` 에는 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Name`|필수 요소. 일정 항목의 이름입니다. 이는 `ScheduleName` 요소의 속성에 해당 `Command` 합니다. 가 명명 된 일정을 참조 하는 경우 해당 `Command` 요소에 지정 된 시간에만 실행 됩니다 `Schedule` . 일정 `FailIf` `BypassIf` 은 지정 된 일정에 따라 이러한 조건부 테스트가 실행 되도록 제한 하는 및 요소와 연결 될 수도 있습니다. 자세한 내용은 [\<Commands> 요소](../deployment/commands-element-bootstrapper.md)를 참조하세요.|  
  
 지정 된 `Schedule` 요소에는 다음 자식 중 하나만 있을 수 있습니다.  
  
## <a name="buildlist"></a>BuildList  
 `BuildList`요소는 부트스트래핑 응용 프로그램이 시작 된 직후에 명령을 실행 하도록 설치 관리자에 지시 합니다.  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage`요소는 지정 된 패키지를 설치 하기 전에 설치 관리자에 게 명령을 실행 하도록 지시 합니다.  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage`요소는 지정 된 패키지가 설치 된 후 설치 관리자에 게 명령을 실행 하도록 지시 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [\<Product> 요소인](../deployment/product-element-bootstrapper.md)   
 [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)
