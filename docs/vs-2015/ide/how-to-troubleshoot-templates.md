---
title: '방법: 템플릿 문제 해결 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c481b2b9c90b15f4cbc709cad89e5b772ad95cee
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477092"
---
# <a name="how-to-troubleshoot-templates"></a>방법: 템플릿 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개발 환경에서 템플릿을 로드할 수 없는 경우 여러 가지 방법으로 문제를 찾을 수 있습니다.

## <a name="validating-the-vstemplate-file"></a>.vstemplate 파일의 유효성 검사
 템플릿에서 .vstemplate 파일이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 템플릿 스키마를 따르지 않으면 해당 템플릿은 **새 프로젝트** 대화 상자에 표시되지 않을 수 있습니다.

#### <a name="to-validate-the-vstemplate-file"></a>.vstemplate 파일의 유효성을 검사하려면

1. 템플릿을 포함하는 .zip 파일을 찾습니다.

2. .zip 파일의 압축을 풉니다.

3. **의 **파일[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 메뉴에서 **열기**를 클릭하고 **파일**을 클릭합니다.

4. 템플릿의 .vstemplate 파일을 선택하고 **열기**를 클릭합니다.

5. .vstemplate 파일의 XML이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 템플릿 스키마에 부합하는지 확인합니다. .vstemplate 스키마에 대한 자세한 내용은 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조하세요.

    > [!NOTE]
    > .vstemplate 파일을 제작하는 동안 IntelliSense 지원을 가져오려면 `xmlns` 특성을 `VSTemplate` 요소에 추가하고 `http://schemas.microsoft.com/developer/vstemplate/2005`의 값을 할당합니다.

6. .vstemplate 파일을 저장한 다음 닫습니다.

7. 템플릿에 포함된 파일을 선택하고, 마우스 오른쪽 단추로 클릭하고, **보내기**를 선택하고, **압축(ZIP) 폴더**를 클릭합니다. 선택한 파일이 .zip 파일로 압축됩니다.

8. 새 .zip 파일을 이전 .zip 파일과 같은 디렉터리에 배치합니다.

9. 추출된 템플릿 파일과 이전 템플릿 .zip 파일을 삭제합니다.

## <a name="monitoring-the-event-log"></a>이벤트 로그 모니터링
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]는 .zip 템플릿 파일을 처리할 때 발생한 오류를 기록합니다. 템플릿에 예상 대로 **새 프로젝트** 대화 상자가 표시되지 않는 경우 **이벤트 뷰어**를 사용하여 문제를 해결할 수 있습니다.

#### <a name="to-locate-template-errors-in-event-viewer"></a>이벤트 뷰어에서 템플릿 오류를 찾으려면

1. Windows에서 **시작**, **제어판**을 차례로 클릭한 다음 **관리 도구**, **이벤트 뷰어**를 차례로 두 번 클릭합니다.

2. 왼쪽 창에서 **애플리케이션**을 클릭합니다.

3. **이라는 **원본`Visual Studio - VsTemplate` 값을 포함하는 이벤트를 검색합니다.

4. 오류를 보려면 템플릿 이벤트를 두 번 클릭합니다.

## <a name="see-also"></a>참고 항목
 [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md) [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
