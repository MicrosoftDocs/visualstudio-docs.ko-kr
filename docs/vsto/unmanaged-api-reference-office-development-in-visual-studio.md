---
title: 관리 되지 않는 API 참조 (Visual Studio에서 Office 개발)
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c1616d24ae9b2c072df4e5708eb98e86611a83d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540987"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>관리 되지 않는 API 참조 (Visual Studio에서 Office 개발)

2007 Microsoft Office 시스템부터 Office 응용 프로그램은 [IManagedAddin interface](../vsto/imanagedaddin-interface.md) 인터페이스를 사용 하 여에 포함 된 VSTO 추가 기능 로더 구성 요소를 호출 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 합니다. 이 구성 요소는 로드 관리 되는 VSTO 추가 기능을 지 원하는 데 사용 됩니다. 이 인터페이스를 구현 하 여 사용자 고유의 VSTO 추가 기능 로더 구성 요소를 만들 수 있습니다.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>단원 내용

[IManagedAddin 인터페이스](../vsto/imanagedaddin-interface.md)

Office 애플리케이션에서 관리되는 VSTO 추가 기능을 로드 및 언로드하기 위해 구현할 수 있는 COM 인터페이스입니다.
