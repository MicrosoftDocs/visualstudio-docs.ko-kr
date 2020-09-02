---
title: 고급 빌드 설정 대화 상자(C#) | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38f4d233c8804bec91d2f7dfd2dc34c6879e8be9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651728"
---
# <a name="advanced-build-settings-dialog-box-c"></a>고급 빌드 설정 대화 상자(C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**프로젝트 디자이너**의 **고급 빌드 설정** 대화 상자를 사용하여 프로젝트의 고급 빌드 구성 속성을 지정합니다. 이 대화 상자는 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 프로젝트에만 적용됩니다.

## <a name="general"></a>일반
 다음 옵션을 사용하여 일반 고급 설정을 설정할 수 있습니다.

 **언어 버전** 사용할 언어의 버전을 지정합니다. 기능 집합은 버전에 따라 다르므로 이 옵션을 사용하여 컴파일러에서 구현된 기능의 하위 집합만 허용하도록 하거나 기존 표준과 호환되는 기능만 사용하도록 설정할 수 있습니다. 이 설정에는 다음과 같은 옵션이 있습니다.

- **ISO-1**

   ISO-1 표준 기능을 대상으로 지정합니다.

- **default**

   현재 버전을 대상으로 지정합니다.

  자세한 내용은 [/langversion (c # 컴파일러 옵션)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94)를 참조 하세요.

  **내부 컴파일러 오류 보고** Microsoft에 컴파일러 오류를 보고할지 여부를 지정합니다. **prompt**(기본값)로 설정되면 내부 컴파일러 오류가 발생할 경우 오류 보고서를 전자 방식으로 Microsoft에 보내는 옵션을 제공하는 프롬프트가 표시됩니다. **send**로 설정되면 오류 보고서가 자동으로 전송됩니다. **queue**로 설정되면 오류 보고서가 대기합니다. **none**으로 설정되면 오류가 컴파일러의 텍스트 출력으로만 보고됩니다. 자세한 내용은 [/errorreport (c # 컴파일러 옵션)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf)를 참조 하세요.

  **산술 연산 오버플로/언더플로 확인** [Checked](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) 또는 [unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) 키워드의 범위에 있지 않고 데이터 형식 범위를 벗어난 값을 생성 하는 정수 산술 문이 런타임 예외를 발생 시키는 지 여부를 지정 합니다. 자세한 내용은 [/checked (c # 컴파일러 옵션)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b)를 참조 하세요.

  **mscorlib.dll을 참조하지 않음** mscorlib.dll을 프로그램으로 가져와 전체 <xref:System> 네임스페이스를 정의할지 여부를 지정합니다. 고유한 <xref:System> 네임스페이스 및 개체를 정의하거나 만들려면 이 상자를 선택합니다. 자세한 내용은 [/nostdlib (c # 컴파일러 옵션)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f)를 참조 하세요.

## <a name="output"></a>출력
 다음 옵션을 사용하여 고급 출력 옵션을 지정할 수 있습니다.

 **디버그 정보** 컴파일러에서 생성 하는 디버깅 정보의 형식을 지정 합니다. 애플리케이션의 디버그 성능을 구성하는 방법에 대한 자세한 내용은 [쉽게 디버깅할 수 있도록 이미지 만들기](https://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3)를 참조하세요. 이 설정에는 다음과 같은 옵션이 있습니다.

- **없음**

   디버깅 정보가 생성되지 않도록 지정합니다.

- **full**

   디버거를 실행 중인 프로그램에 연결할 수 있습니다.

- **pdbonly**

   디버거에서 프로그램이 시작되는 경우 소스 코드 디버깅이 가능하지만, 실행 중인 프로그램이 디버거에 연결되는 경우 어셈블러만 표시됩니다.

  자세한 내용은 [/debug (c # 컴파일러 옵션)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969)를 참조 하세요.

  **파일 맞춤** 출력 파일의 섹션 크기를 지정합니다. 유효한 값은 **512**, **1024**, **2048**, **4096**및 **8192**입니다. 이러한 값은 바이트 단위로 측정됩니다. 각 섹션은 이 값의 배수인 경계에 맞춰지고 출력 파일 크기에 영향을 미칩니다. 자세한 내용은 [/filealign (c # 컴파일러 옵션)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073)를 참조 하세요.

  **DLL 기준 주소** DLL을 로드할 기본 설정 기준 주소를 지정 합니다. DLL에 대한 기본 기준 주소는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 공용 언어 런타임에 의해 설정됩니다. 자세한 내용은 [/baseaddress (c # 컴파일러 옵션)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [C# 컴파일러 옵션](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44) [프로젝트 디자이너, 빌드 페이지(C#)](../../ide/reference/build-page-project-designer-csharp.md)
