---
title: 안전한 배포
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c838eddea5b3118c28fb33411a8c58a19d7b4a2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810956"
---
# <a name="secure-deployment"></a>안전한 배포
  Office 솔루션을 만들 때 개발 컴퓨터는 프로젝트의 코드를 실행할 수 있도록 자동으로 업데이트 됩니다. 그러나 솔루션을 배포할 때는 인증서를 사용 하 여 솔루션에 서명 하거나 신뢰 프롬프트 키를 사용 하 여 신뢰 결정의 기반이 되는 증명 정보를 제공 해야 합니다 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . 자세한 내용은 [Office 솔루션에 신뢰 부여](../vsto/granting-trust-to-office-solutions.md)를 참조 하세요.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 문서 수준 사용자 지정의 경우 문서를 네트워크 위치에 배포 하는 경우 Office 응용 프로그램의 보안 센터에 있는 신뢰할 수 있는 위치 목록에도 문서 위치를 추가 해야 합니다. 최종 사용자 컴퓨터에 대 한 문서 사용 권한을 설정 하는 방법에 대 한 자세한 내용은 [문서에 신뢰 부여](../vsto/granting-trust-to-documents.md)를 참조 하세요.

## <a name="prevent-office-solutions-from-running-code"></a>Office 솔루션의 코드 실행 방지
 관리자는 레지스트리를 사용 하 여 모든 Office 솔루션이 컴퓨터에서 실행 되지 않도록 할 수 있습니다. 관리 코드 확장이 있는 Office 솔루션을 열면 Visual Studio Tools for Office 런타임은 `Disabled` 컴퓨터의 다음 레지스트리 키 중 하나에 이름이 있는 항목이 있는지 여부를 확인 합니다.

- **HKEY_CURRENT_USER \Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE \Software\Microsoft\VSTO**

  Office 솔루션에서 코드를 실행 하지 않도록 하려면 다음 `Disabled` 레지스트리 키 중 하나 또는 둘 다에 항목을 만들고에 대해 다음 데이터 형식 및 값 중 하나를 지정 합니다 `Disabled` .

- "0"이 아닌 임의의 문자열로 설정 된 REG_SZ 또는 REG_EXPAND_SZ입니다.

- 0이 아닌 값으로 설정 된 REG_DWORD입니다.

  Office 솔루션에서 코드를 실행할 수 있도록 하려면 두 항목을 모두 `Disabled` 0으로 설정 하거나 레지스트리 항목을 삭제 합니다.

## <a name="see-also"></a>추가 정보
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 솔루션을 실행 하거나 호스트할 컴퓨터 준비](/previous-versions/bb772092(v=vs.110))
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)