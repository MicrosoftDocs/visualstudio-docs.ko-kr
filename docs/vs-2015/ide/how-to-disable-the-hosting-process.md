---
title: '방법: 호스팅 프로세스 비활성화 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95dcd7da113bfe996d00e617b7c8e2f9b68864d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667969"
---
# <a name="how-to-disable-the-hosting-process"></a>How to: Disable the Hosting Process
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

호스팅 프로세스를 사용하면 특정 API에 대한 호출에 영향이 있을 수 있습니다. 이 경우 올바른 결과를 반환하기 위해 호스팅 프로세스를 사용하지 않도록 설정해야 합니다.

### <a name="to-disable-the-hosting-process"></a>호스팅 프로세스를 사용하지 않도록 설정하려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 실행 가능 프로젝트를 엽니다. 실행 파일을 생성하지 않는 프로젝트(예: 클래스 라이브러리 또는 서비스 프로젝트)에는 이 옵션이 없습니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

3. **디버그** 탭을 클릭합니다.

4. **Visual Studio 호스팅 프로세스 사용** 확인란을 선택 취소합니다.

   호스팅 프로세스가 사용하지 않도록 설정되면 여러 디버깅 기능을 사용할 수 없으며 성능 저하가 발생합니다. 자세한 내용은 [디버깅 및 호스팅 프로세스](../debugger/debugging-and-the-hosting-process.md)를 참조하세요.

   일반적으로 호스팅 프로세스는 사용하지 않습니다.

- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 애플리케이션 디버깅을 시작하는 데 필요한 시간이 증가합니다.

- 디자인 타임 식 계산을 사용할 수 없습니다.

- 부분 신뢰 디버깅을 사용할 수 없습니다.

## <a name="see-also"></a>관련 항목
 [응용 프로그램 개발 중](https://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6) [에 디버깅 및 호스팅 프로세스](../debugger/debugging-and-the-hosting-process.md) [호스팅 프로세스 (vshost.exe)](../ide/hosting-process-vshost-exe.md) 빌드
