---
title: 64 비트 디버거 COM 클래스 등록 마이그레이션 | Microsoft Docs
description: HKEY_CLASSES_ROOT에 쓰지 않고 디버거 확장을 위해 msvsmon에 COM 클래스를 등록 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.workload:
- greggm
ms.openlocfilehash: adc1db57de2167ff3caa0e87e1075c8ff5b462e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886719"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64 비트 디버거 COM 클래스 등록 마이그레이션

Regasm, regsvr32를 사용 하 여 HKEY_CLASSES_ROOT에 COM 클래스를 등록 하거나 레지스트리에 직접 쓰고 *msvsmon.exe* (원격 디버거)에 로드 된 디버거 확장의 경우, 이제 HKEY_CLASSES_ROOT에 쓰지 않고도이 등록을 msvsmon에 제공할 수 있습니다. 이는 *msvsmon.exe* 프로세스에서 로드 하도록 구성 된 레거시 .net 디버거 식 계산기 또는 디버그 엔진에 영향을 줍니다.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

이 방법을 사용 하려면 *msvsmon (InstallDir: \Common7\IDE\Remote debugger\x64 or *) 옆에 *있는 파일에.msvsmon-comclass-def.js** 를 추가 합니다.

다음은 관리 되는 클래스와 네이티브 클래스 하나를 등록 하는 msvsmon-comclass def 파일의 예입니다.

파일 이름: *MyCompany.MyExample.msvsmon-comclass-def.js*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
