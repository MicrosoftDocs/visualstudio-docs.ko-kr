---
title: '방법: Office 주 interop 어셈블리 설치'
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6f90b568f98abe5026525a60723efb59f737235
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544783"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>방법: Office 주 interop 어셈블리 설치
  Office를 설치할 때 Microsoft Office PIA(주 interop 어셈블리)를 설치합니다.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Office를 설치할 때 PIA를 설치하려면

1. .NET Framework 2.0 이상 버전이 설치되어 있는지 확인합니다.

2. Microsoft Office를 설치 하 고 확장할 응용 프로그램에 대해 **.Net 프로그래밍 지원** 기능이 선택 되어 있는지 확인 합니다 .이 기능은 기본 설치에 포함 되어 있습니다.

    > [!WARNING]
    > 기본적으로 솔루션을 빌드할 때 PIA가 솔루션에 포함 되므로 VSTO 추가 기능 또는 사용자 지정을 사용 하기 위한 필수 구성 요소로 사용자에 게 Pia를 배포할 필요가 없습니다.

## <a name="see-also"></a>참조
- [Office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)
- [방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [방법: Office 솔루션을 개발할 수 있도록 컴퓨터 구성](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [방법: Visual Studio Tools for Office 런타임 재배포 가능 패키지 설치](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Visual Studio에서 Office 개발 &#40;시작&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
