---
title: Vbc 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6edc8b246055dcd8efdb32f4118f81a535635d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683828"
---
# <a name="vbc-task"></a>Vbc 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

실행 파일(.exe), 동적 링크 라이브러리(.dll) 또는 코드 모듈(.netmodule)을 생성하는 vbc.exe를 래핑합니다. vbc.exe에 대 한 자세한 내용은 [명령줄 컴파일러 Visual Basic](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)를 참조 하세요.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `Vbc` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`AdditionalLibPaths`|선택적 `String[]` 매개 변수입니다.<br /><br /> References 특성에 지정된 어셈블리를 검색하는 추가 폴더를 지정합니다.|  
|`AddModules`|선택적 `String[]` 매개 변수입니다.<br /><br /> 컴파일러에서 지정된 파일의 모든 형식 정보를 현재 컴파일하고 있는 프로젝트에 사용할 수 있도록 합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/addmodule](https://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) 스위치에 해당 합니다.|  
|`BaseAddress`|선택적 `String` 매개 변수입니다.<br /><br /> DLL의 기준 주소를 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/baseaddress](https://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) 스위치에 해당 합니다.|  
|`CodePage`|선택적 `Int32` 매개 변수입니다.<br /><br /> 컴파일할 때 모든 소스 코드 파일에 사용할 코드 페이지를 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/codepage](https://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) 스위치에 해당 합니다.|  
|`DebugType`|선택적 `String[]` 매개 변수입니다.<br /><br /> 컴파일러에서 디버깅 정보를 생성하도록 합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> 기본값은 `full`로, 디버거를 실행 중인 프로그램에 연결할 수 있습니다. `pdbonly` 값을 지정하면 디버거에서 프로그램이 시작되는 경우 소스 코드 디버깅이 가능하지만, 실행 중인 프로그램이 디버거에 연결되는 경우에만 어셈블리 언어 코드가 표시됩니다. 자세한 내용은 [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2)를 참조 하세요.|  
|`DefineConstants`|선택적 `String[]` 매개 변수입니다.<br /><br /> 조건부 컴파일러 상수를 정의합니다. 기호/값 쌍은 세미콜론으로 구분되고 다음 구문을 사용하여 지정됩니다.<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> 이 매개 변수는 vbc.exe 컴파일러의 [/define](https://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) 스위치에 해당 합니다.|  
|`DelaySign`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 작업에서 공개 키를 어셈블리에 저장합니다. `false`인 경우 작업에서 어셈블리에 완전히 서명합니다. 기본값은 `false`입니다. 이 매개 변수는 `KeyFile` 매개 변수나 `KeyContainer` 매개 변수와 함께 사용하는 경우에만 영향을 미칩니다. 이 매개 변수는 vbc.exe 컴파일러의 [/delaysign](https://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) 스위치에 해당 합니다.|  
|`DisabledWarnings`|선택적 `String` 매개 변수입니다.<br /><br /> 지정한 경고를 표시하지 않습니다. 경고 식별자의 숫자 부분만 지정하면 됩니다. 경고가 여러 개인 경우 세미콜론으로 구분할 수 있습니다. 이 매개 변수는 vbc.exe 컴파일러의 [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) 스위치에 해당 합니다.|  
|`DocumentationFile`|선택적 `String` 매개 변수입니다.<br /><br /> 지정된 XML 파일에 대해 문서 주석을 처리합니다. 이 매개 변수는 `GenerateDocumentation` 특성을 재정의합니다. 자세한 내용은 [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65)를 참조 하세요.|  
|`EmitDebugInformation`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 작업에서 디버깅 정보를 생성하여 .pdb 파일에 저장합니다. 자세한 내용은 [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2)를 참조 하세요.|  
|`ErrorReport`|선택적 `String` 매개 변수입니다.<br /><br /> 작업에서 내부 컴파일러 오류를 보고하는 방식을 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> `prompt`가 지정되고 내부 컴파일러 오류가 발생하면 사용자에게 오류 데이터를 Microsoft에 보낼지 여부를 묻는 메시지가 표시됩니다.<br /><br /> `send`가 지정되고 내부 컴파일러 오류가 발생하면 작업에서 오류 데이터를 Microsoft에 보냅니다.<br /><br /> 기본값은 `none`으로, 오류를 텍스트 출력으로만 보고합니다.<br /><br /> 이 매개 변수는 vbc.exe 컴파일러의 [/errorreport](https://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) 스위치에 해당 합니다.|  
|`FileAlignment`|선택적 `Int32` 매개 변수입니다.<br /><br /> 출력 파일의 섹션에 맞출 위치(바이트)를 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> 이 매개 변수는 vbc.exe 컴파일러의 [/filealign](https://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) 스위치에 해당 합니다.|  
|`GenerateDocumentation`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 문서 정보를 생성하여 이 정보를 작업에서 만든 실행 파일이나 라이브러리의 이름과 함께 XML 파일에 저장합니다. 자세한 내용은 [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65)를 참조 하세요.|  
|`Imports`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 지정된 항목 컬렉션에서 네임스페이스를 가져옵니다. 이 매개 변수는 vbc.exe 컴파일러의 [/imports](https://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) 스위치에 해당 합니다.|  
|`KeyContainer`|선택적 `String` 매개 변수입니다.<br /><br /> 암호화 키 컨테이너의 이름을 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/keycontainer](https://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) 스위치에 해당합니다.|  
|`KeyFile`|선택적 `String` 매개 변수입니다.<br /><br /> 암호화 키를 포함하는 파일 이름을 지정합니다. 자세한 내용은 [/keyfile](https://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8)을 참조 하십시오.|  
|`LangVersion`|선택적 [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) 매개 변수입니다.<br /><br /> 언어 버전으로 “9” 또는 “10”을 지정합니다.|  
|`LinkResources`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 출력 파일에 .NET Framework 리소스에 대한 링크를 만듭니다. 리소스 파일은 출력 파일에 저장되지 않습니다. 이 매개 변수는 vbc.exe 컴파일러의 [/linkresource](https://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) 스위치에 해당 합니다.|  
|`MainEntryPoint`|선택적 `String` 매개 변수입니다.<br /><br /> `Sub Main` 프로시저가 포함된 클래스 또는 모듈을 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) 스위치에 해당합니다.|  
|`ModuleAssemblyName`|선택적 `String` 매개 변수입니다.<br /><br /> 이 모듈이 속한 어셈블리를 지정합니다.|  
|`NoConfig`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 컴파일러에서 vbc.rsp 파일을 사용하지 않도록 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/noconfig](https://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) 매개 변수에 해당 합니다.|  
|`NoLogo`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 컴파일러 배너 정보를 표시하지 않습니다. 이 매개 변수는 vbc.exe 컴파일러의 [/nologo](https://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) 스위치에 해당 합니다.|  
|`NoStandardLib`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 컴파일러에서 표준 라이브러리를 참조하지 않도록 합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/nostdlib](https://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) 스위치에 해당 합니다.|  
|`NoVBRuntimeReference`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 내부 전용입니다. true이면 Microsoft.VisualBasic.dll에 대한 자동 참조를 차단합니다.|  
|`NoWarnings`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 작업에서 모든 경고를 표시하지 않습니다. 자세한 내용은 [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83)을 참조 하세요.|  
|`Optimize`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 컴파일러 최적화를 사용할 수 있습니다. 이 매개 변수는 vbc.exe 컴파일러의 [/optimize](https://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) 스위치에 해당 합니다.|  
|`OptionCompare`|선택적 `String` 매개 변수입니다.<br /><br /> 문자열 비교 방법을 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `binary`<br />-   `text`<br /><br /> `binary` 값은 작업에서 이진 문자열 비교를 사용하도록 지정합니다. `text` 값은 작업에서 텍스트 문자열 비교를 사용하도록 지정합니다. 이 매개 변수의 기본값은 `binary`입니다. 이 매개 변수는 vbc.exe 컴파일러의 [/shcompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) 스위치에 해당 합니다.|  
|`OptionExplicit`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 명시적 변수 선언이 필요합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/she](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) 스위치에 해당 합니다.|  
|`OptionInfer`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 변수 형식 유추를 허용합니다.|  
|`OptionStrict`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 작업에서 엄격한 형식 의미 체계를 적용하여 암시적 형식 변환을 제한합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/svstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) 스위치에 해당 합니다.|  
|`OptionStrictType`|선택적 `String` 매개 변수입니다.<br /><br /> 경고를 생성하는 엄격한 형식 의미 체계를 지정합니다. 현재는 “custom”만 지원됩니다. 이 매개 변수는 vbc.exe 컴파일러의 [/svstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) 스위치에 해당 합니다.|  
|`OutputAssembly`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 출력 파일의 이름을 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/out](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) 스위치에 해당 합니다.|  
|`Platform`|선택적 `String` 매개 변수입니다.<br /><br /> 출력 파일의 대상으로 프로세서 플랫폼을 지정합니다. 이 매개 변수는 값 `x86`, `x64`, `Itanium` 또는 `anycpu`를 사용할 수 있습니다. 기본값은 `anycpu`입니다. 이 매개 변수는 vbc.exe 컴파일러의 [/platform](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) 스위치에 해당 합니다.|  
|`References`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 작업에서 지정된 항목의 공용 형식 정보를 현재 프로젝트로 가져옵니다. 이 매개 변수는 vbc.exe 컴파일러의 [/reference](https://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) 스위치에 해당 합니다.|  
|`RemoveIntegerChecks`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 정수 오버플로 오류 검사를 사용할 수 없습니다. 기본값은 `false`입니다. 이 매개 변수는 vbc.exe 컴파일러의 [/removeintchecks](https://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) 스위치에 해당 합니다.|  
|`Resources`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> .NET Framework 리소스를 출력 파일에 포함합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/resource](https://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) 스위치에 해당 합니다.|  
|`ResponseFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 이 작업에 대한 명령을 포함하는 지시 파일을 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [@(지시 파일 지정)](https://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) 옵션에 해당합니다.|  
|`RootNamespace`|선택적 `String` 매개 변수입니다.<br /><br /> 모든 형식 선언에 대한 루트 네임스페이스를 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/rootnamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) 스위치에 해당 합니다.|  
|`SdkPath`|선택적 `String` 매개 변수입니다.<br /><br /> mscorlib.dll 및 microsoft.visualbasic.dll의 위치를 지정합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/sdkpath](https://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) 스위치에 해당 합니다.|  
|`Sources`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 소스 파일을 하나 이상 지정합니다.|  
|`TargetCompactFramework`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 작업에서 [!INCLUDE[Compact](../includes/compact-md.md)]를 대상으로 지정합니다. 이 스위치는 vbc.exe 컴파일러의 [/netcf](https://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) 스위치에 해당 합니다.|  
|`TargetType`|선택적 `String` 매개 변수입니다.<br /><br /> 출력 파일의 파일 형식을 지정합니다. 이 매개 변수는 각각 코드 라이브러리를 만드는 `library`, 콘솔 애플리케이션을 만드는 `exe`, 모듈을 만드는 `module` 또는 Windows 프로그램을 만드는 `winexe`를 값으로 가질 수 있습니다. 기본값은 `library`입니다. 이 매개 변수는 vbc.exe 컴파일러의 [/target](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) 스위치에 해당 합니다.|  
|`Timeout`|선택적 `Int32` 매개 변수입니다.<br /><br /> 작업 실행 파일이 얼마 후에 종료될 지를 밀리초 단위로 지정합니다. 기본값은 시간 제한이 없음을 나타내는 `Int.MaxValue`입니다.|  
|`ToolPath`|선택적 `String` 매개 변수입니다.<br /><br /> 작업에서 내부 실행 파일(vbc.exe)을 로드할 위치를 지정합니다. 이 매개 변수를 지정하지 않으면 작업에서는 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행하고 있는 버전의 Framework에 해당하는 SDK 설치 경로가 사용됩니다.|  
|`TreatWarningsAsErrors`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 모든 경고가 오류로 처리됩니다. 자세한 내용은 [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)를 참조 하세요.|  
|`UseHostCompilerIfAvailable`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 사용 가능한 경우 In Process 컴파일러 개체를 사용하도록 작업에 지시합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서만 사용됩니다.|  
|`Utf8Output`|선택적 `Boolean` 매개 변수입니다.<br /><br /> UTF-8 인코딩을 사용하여 컴파일러 출력을 기록합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/utf8output](https://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) 스위치에 해당 합니다.|  
|`Verbosity`|선택적 `String` 매개 변수입니다.<br /><br /> 컴파일러의 출력에 대한 자세한 정도를 지정합니다. 자세한 정도는 `Quiet`, `Normal`(기본값) 또는 `Verbose`일 수 있습니다.|  
|`WarningsAsErrors`|선택적 `String` 매개 변수입니다.<br /><br /> 오류로 처리할 경고 목록을 지정합니다. 자세한 내용은 [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)를 참조 하세요.<br /><br /> 이 매개 변수는 `TreatWarningsAsErrors` 매개 변수를 재정의합니다.|  
|`WarningsNotAsErrors`|선택적 `String` 매개 변수입니다.<br /><br /> 오류로 처리하지 않을 경고 목록을 지정합니다. 자세한 내용은 [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)를 참조 하세요.<br /><br /> 이 매개 변수는 `TreatWarningsAsErrors` 매개 변수가 `true`로 설정된 경우에만 유용합니다.|  
|`Win32Icon`|선택적 `String` 매개 변수입니다.<br /><br /> 파일 탐색기에서 출력 파일을 원하는 모양으로 표시하는 .ico 파일을 어셈블리에 삽입합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) 스위치에 해당 합니다.|  
|`Win32Resources`|선택적 `String` 매개 변수입니다.<br /><br /> Win32 리소스(.res) 파일을 출력 파일에 삽입합니다. 이 매개 변수는 vbc.exe 컴파일러의 [/win32resource](https://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) 스위치에 해당 합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.ToolTask> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Tooltaskextension 기본 클래스](../msbuild/tooltaskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예  
 다음 예제에서는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 프로젝트를 컴파일합니다.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>관련 항목  
 [Visual Basic 명령줄 컴파일러](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
