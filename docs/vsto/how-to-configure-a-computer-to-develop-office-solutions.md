---
title: '방법: Office 솔루션을 개발할 수 있도록 컴퓨터 구성'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93c8287b0b2234c45056829ba78d993658b0428d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585499"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>방법: Office 솔루션을 개발할 수 있도록 컴퓨터 구성
  Visual Studio의 Microsoft Office 개발자 도구를 사용할 수 있도록 개발 컴퓨터를 구성하려면 이 항목의 지침을 따릅니다. 이러한 단계를 수행하려면 개발 컴퓨터에 대한 관리자 권한이 있어야 합니다.

### <a name="to-configure-the-development-computer"></a>개발 컴퓨터를 구성하려면

1. Office 개발자 도구가 포함된 Visual Studio 버전을 설치합니다. Office 개발자 도구는 기본적으로 설치됩니다. 설치할 기능을 선택 하 여 Visual Studio 설치를 사용자 지정 하는 경우 설치 하는 동안 **Microsoft Office 개발자 도구** 가 선택 되어 있는지 확인 합니다. Office 개발자 도구가 포함 된 Visual Studio 버전에 대 한 자세한 내용은 [office 솔루션을 개발할 수 있도록 컴퓨터 구성](../vsto/configuring-a-computer-to-develop-office-solutions.md)을 참조 하세요.

2. Visual Studio의 Office 개발자 도구에서 지원하는 Office 버전을 설치합니다. 자세한 내용은 [Office 솔루션을 개발할 수 있도록 컴퓨터 구성](../vsto/configuring-a-computer-to-develop-office-solutions.md)을 참조 하세요.

     설치하는 Office 버전에 대한 PIA도 설치해야 합니다. PIA는 기본적으로 Office와 함께 설치됩니다. Office 설치 프로그램을 수정 하는 경우 대상으로 지정할 응용 프로그램에 대해 **.Net 프로그래밍 지원** 기능이 선택 되어 있는지 확인 합니다.

3. 영어 버전의 Visual Studio가 있지만 영어가 아닌 Windows 설정을 사용 하는 경우 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 언어 팩을 설치 하 여 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] windows와 동일한 언어로 메시지를 볼 수 있습니다. 영어가 아닌 버전의 Visual Studio에서는 해당 언어 팩을 자동으로 설치합니다. [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=54246)에서 언어 팩을 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 Office 개발 &#40;시작&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [방법: Visual Studio Tools for Office 런타임 재배포 가능 패키지 설치](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [방법: Office 주 interop 어셈블리 설치](../vsto/how-to-install-office-primary-interop-assemblies.md)
