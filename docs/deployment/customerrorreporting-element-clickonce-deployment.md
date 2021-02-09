---
title: '&lt;customErrorReporting &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
description: CustomErrorReporting 요소는 예외 스택을 표시 하는 오류 대화 상자 대신 오류가 발생 하는 경우 표시할 URI를 지정 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b168b3bcb90ae758609698de306928eb7e13d909
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888487"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting &gt; 요소 (ClickOnce 배포)
오류가 발생할 때 표시할 URI를 지정합니다.

## <a name="syntax"></a>구문

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>설명
 이 요소는 선택적입니다. 없으면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 예외 스택을 보여 주는 오류 대화 상자가 표시 됩니다. 요소가 있으면 `customErrorReporting` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 는 매개 변수로 표시 된 URI를 대신 표시 `uri` 합니다. 대상 URI에는 외부 예외 클래스, 내부 예외 클래스 및 내부 예외 메시지가 매개 변수로 포함 됩니다.

 이 요소를 사용 하 여 오류 보고 기능을 응용 프로그램에 추가할 수 있습니다. 생성 된 URI에는 오류 유형에 대 한 정보가 포함 되어 있으므로 웹 사이트에서 해당 정보를 구문 분석 하 여 적절 한 문제 해결 화면 등을 표시할 수 있습니다.

## <a name="example"></a>예제
 다음 코드 조각은 생성 된 `customErrorReporting` URI와 함께 요소를 보여 줍니다.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>참고 항목
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)