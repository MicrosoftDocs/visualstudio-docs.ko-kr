---
title: '방법: 워크플로 프로젝트에 새 항목 추가 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46f6e9daafc2688b9bea75cba9eddd8c8a53c9bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656664"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>방법: 워크플로 프로젝트에 새 항목 추가(레거시)
[!INCLUDE[wfd1](../includes/wfd1-md.md)] 또는 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 대상으로 하는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 제공 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용하여 워크플로 프로젝트를 만든 후에는 [!INCLUDE[wf](../includes/wf-md.md)] 항목과 그 밖의 친숙한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 항목을 프로젝트에 추가할 수 있습니다.

 다음 표에서는 워크플로 프로젝트에 추가할 수 있는 [!INCLUDE[wf2](../includes/wf2-md.md)] 항목을 보여 줍니다.

|항목|설명|
|----------|-----------------|
|활동|디자이너 코드 파일에 동작 정의가 있고 별도의 코드 파일에 사용자 코드가 있는 동작|
|동작(코드 분리)|워크플로 마크업으로 표현되었고 별도의 코드 파일에 사용자 코드가 있는 동작 정의|
|순차 워크플로(코드)|디자이너 코드 파일에 워크플로 정의가 있고 별도의 코드 파일에 사용자 코드가 있는 순차 워크플로|
|순차 워크플로(코드 분리)|워크플로 정의가 워크플로 마크업으로 표현되었고 별도의 코드 파일에 사용자 코드가 있는 순차 워크플로|
|상태 시스템 워크플로(코드)|디자이너 코드 파일에 워크플로 정의가 있고 별도의 코드 파일에 사용자 코드가 있는 상태 시스템 워크플로|
|상태 시스템 워크플로(코드 분리)|워크플로 정의가 워크플로 마크업으로 표현되었고 별도의 코드 파일에 사용자 코드가 있는 상태 시스템 워크플로|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>워크플로 프로젝트에 새 항목을 추가하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭 합니다.

     **새 항목 추가** 대화 상자가 열립니다.

2. 항목을 선택합니다.

     위의 표에서는 사용 가능한 Windows Workflow Foundation 선택 항목을 보여 줍니다.

3. **추가** 를 클릭 하 여 워크플로 프로젝트에 항목을 추가 합니다.

## <a name="see-also"></a>관련 항목
 [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md)