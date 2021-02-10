---
title: 지원되는 코드 변경(C++) | Microsoft Docs
description: Visual Studio에서 C++ 프로젝트를 디버그하는 동안 편집하며 계속하기 기능을 사용하는 경우 지원되는 코드 변경 내용을 이해합니다.
ms.custom: SEO-VS-2020
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: d000d2757321701c2e14427c6bbb4d3e4164d26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876305"
---
# <a name="supported-code-changes-c"></a>지원되는 코드 변경(C++)
C++ 프로젝트의 편집하며 계속하기에서는 대부분의 코드 변경 유형을 처리합니다. 그러나 일부 변경 내용은 프로그램을 실행하는 동안 적용할 수 없습니다. 이러한 변경 내용을 적용하려면 실행을 중지하고 새로운 버전의 코드를 빌드해야 합니다.

 Visual Studio에서 C++의 편집하며 계속하기를 사용하는 방법에 대한 자세한 내용은 [편집하며 계속하기(C++)](../debugger/edit-and-continue-visual-cpp.md)를 참조하세요.

## <a name="requirements"></a><a name="BKMK_Requirements"></a> 요구 사항
### <a name="build-settings-project--properties"></a>빌드 설정(프로젝트 > 속성):
  1. **C/C++ > 일반 > 디버그 정보 형식**: 편집하며 계속하기용 프로그램 데이터베이스(`/ZI`)
  2. **C/C++ > 코드 생성 > 최소 다시 빌드 사용**: 예(`/Gm`)
  3. **링커 > 일반 > 증분 링크 사용**: 예(`/INCREMENTAL`)

     모든 호환되지 않는 링커 설정(예: `/SAFESEH` 또는 `/OPT:`...)은 빌드 중에 경고 _LNK4075_ 가 발생해야 합니다.  
     예: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>디버거 설정(디버그 > 옵션 > 일반):
  - 네이티브 편집하며 계속하기 사용

     편집하며 계속하기 중 호환되지 않는 컴파일러 또는 링커 설정에서 오류가 발생합니다.  
     예: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> 지원되지 않는 변경 사항
 디버깅 세션 중에 적용할 수 없는 C/C++ 변경 내용은 다음과 같습니다. 이러한 변경을 수행하고 코드 변경 내용을 적용하려고 하면 **출력** 창에 오류 또는 경고 메시지가 나타납니다.

- 대부분의 전역 또는 정적 데이터 변경

- 다른 컴퓨터에서 복사하여 로컬로 빌드하지 않은 실행 파일의 변경

- 개체(예: 클래스의 데이터 멤버)의 레이아웃에 영향을 주는 데이터 형식의 변경

- 64KB를 초과하는 새 코드나 데이터 추가

- 명령 포인터 앞의 위치에 생성자가 필요한 변수 추가

- 런타임 초기화가 필요한 코드에 영향을 주는 변경

- 특정한 경우에 예외 처리기 추가

- 리소스 파일의 변경

- 읽기 전용 파일의 코드 변경

- 해당하는 PDB 파일이 없는 코드의 변경

- 개체 파일이 없는 코드의 변경

* 다음과 같은 람다를 수정:
  - 정적 또는 전역 멤버를 포함합니다.
  - std::function에 전달됩니다. 이 경우 진정한 ODR 위반이 초래되고 C1092가 발생합니다.

- 편집하며 계속하기는 정적 라이브러리를 업데이트하지 않습니다. 정적 라이브러리에서 변경하면 이전 버전을 사용하여 실행이 계속되고 경고가 발생하지 않습니다.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> 지원되지 않는 시나리오
 다음과 같은 디버깅 시나리오에서는 C/C++의 편집하며 계속하기를 사용할 수 없습니다.

- [/Zo(최적화된 디버깅 향상)](/cpp/build/reference/zo-enhance-optimized-debugging)로 컴파일한 네이티브 앱 디버그

- Visual Studio 2015 업데이트 1보다 이전 버전의 Visual Studio에서 UWP 앱 또는 구성 요소 디버그. Visual Studio 2015 업데이트 1부터는 `/ZI` 스위치로 `/bigobj` 컴파일러 스위치를 지원하기 때문에 UWP C++ 앱 및 DirectX 앱에서 편집하며 계속하기를 사용할 수 있습니다. `/FASTLINK` 컴파일러 스위치를 지원하기 때문에 Windows 스토어 C++ 앱 및 DirectX 앱에서 편집하며 계속하기를 사용할 수 있습니다.

- 8/8.1 스토어 앱 디버깅. 이러한 프로젝트는 VC 120 도구 집합 및 C/C++ `/bigobj` 스위치를 사용합니다. `/bigobj`를 사용한 편집하며 계속하기는 VC 140 도구 집합에서만 지원됩니다.

- Windows 98에서 디버깅

- 혼합 모드(네이티브/관리) 디버깅

- JavaScript 디버깅

- SQL 디버깅

- 덤프 파일 디버깅

- **처리되지 않은 예외에 대한 호출 스택 해제** 옵션을 선택하지 않은 상태에서 처리되지 않은 예외가 발생한 후 코드 편집

- **디버그** 메뉴에서 **시작** 을 선택하여 앱을 실행하는 대신 **연결 대상** 을 사용하여 앱 디버깅

- 최적화된 코드 디버깅

- 빌드 오류가 발생하여 새 버전을 빌드하는 데 실패한 후 이전 버전의 코드 디버깅

- 사용자 지정 컴파일러(*cl.exe*) 경로를 사용. 편집하며 계속하기 중에 파일을 다시 컴파일하는 경우 보안을 위해 Visual Studio는 항상 설치된 컴파일러를 사용합니다. 사용자 지정 컴파일러 경로를 사용하는 경우(예를 들어 `*.props` 파일의 사용자 지정 `$(ExecutablePath)` 변수를 사용) 경고가 표시되고 Visual Studio가 동일한 버전/아키텍처의 설치된 컴파일러를 사용하도록 대체됩니다.

- FASTBuild 빌드 시스템. FASTBuild는 현재 "최소 다시 빌드 사용(`/Gm`)" 컴파일러 스위치와 호환되지 않으므로 편집하며 계속하기가 지원되지 않습니다.

- 레거시 아키텍처/VC 도구 집합. VC 140 도구 집합에서는 기본 디버거가 X86 및 X64 애플리케이션 모두에서 편집하며 계속하기를 지원합니다. 레거시 도구 집합은 X86 애플리케이션만 지원합니다. VC 120보다 이전의 도구 집합은 편집하며 계속하기를 사용하려면 "_디버그 > 옵션 > 일반 >_ 기본 호환성 모드 사용"을 선택하여 레거시 디버거를 사용해야 합니다.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> 링크 제한 사항

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> 편집하며 계속하기를 사용하지 않도록 설정하는 링커 옵션
 다음 링커 옵션을 사용하면 편집하며 계속하기가 비활성화됩니다.

- **/OPT:REF**, **/OPT:ICF** 또는 **/INCREMENTAL:NO** 를 설정하면 다음 경고가 나타나고 편집하며 계속하기가 비활성화됩니다.  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- **/ORDER**, **/RELEASE** 또는 **/FORCE** 를 설정하면 다음 경고가 나타나고 편집하며 계속하기가 비활성화됩니다.  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- 프로그램 데이터베이스 파일(.pdb)을 작성하지 않는 옵션을 설정하면 특별한 경고 없이 편집하며 계속하기가 비활성화됩니다.

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> 자동 다시 링크 제한 사항
 기본적으로 편집하며 계속하기는 디버깅 섹션의 끝에서 프로그램을 다시 링크하여 실행 가능한 업데이트를 만듭니다.

 편집하며 계속하기를 사용하면 원래 빌드 위치 이외의 위치에서 디버깅하는 경우 프로그램을 다시 링크할 수 없으며 수동으로 다시 빌드해야 한다는 메시지가 나타납니다.

 편집하며 계속하기는 정적 라이브러리를 다시 빌드하지 않습니다. 편집하며 계속하기를 사용하여 정적 라이브러리를 변경한 경우에는 수동으로 라이브러리를 다시 빌드하고 해당 라이브러리를 사용하여 앱을 다시 링크해야 합니다.

 편집하며 계속하기는 사용자 지정 빌드 단계를 호출하지 않습니다. 프로그램에서 사용자 지정 빌드 단계를 사용할 경우 이를 호출하려면 수동으로 다시 빌드해야 합니다. 이 경우 편집하며 계속하기 이후 다시 링크되지 않도록 하면 수동으로 다시 빌드할 수 있습니다.

 **편집하며 계속하기를 실행한 후 다시 링크하지 않으려면**

1. **디버그** 메뉴에서 **옵션 및 설정** 을 선택합니다.

2. **옵션** 대화 상자의 **디버깅** 노드에서 **편집하며 계속하기** 노드를 선택합니다.

3. **디버깅 후 코드 변경 내용 다시 링크** 확인란의 선택을 취소합니다.

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> 미리 컴파일된 헤더 제한 사항
 기본적으로 편집하며 계속하기는 코드 변경 처리 속도를 높이기 위해 미리 컴파일된 헤더를 백그라운드에서 로드한 다음 처리합니다. 미리 컴파일된 헤더를 로드하려면 실제 메모리를 할당해야 하는데, RAM이 한정된 시스템에서 컴파일하는 경우 문제가 될 수 있습니다. Windows 작업 관리자를 사용하여 디버그하는 동안 사용 가능한 실제 메모리의 양을 확인하면 이 작업이 문제가 될 수 있는지 확인할 수 있습니다. 실제 메모리 양이 미리 컴파일된 헤더의 크기보다 큰 경우에 편집하며 계속하기에는 문제가 없습니다. 실제 메모리 양이 미리 컴파일된 헤더의 크기보다 작은 경우에는 미리 컴파일된 헤더를 백그라운드에서 로드하지 않고 편집하며 계속하기를 할 수 있습니다.

 **편집하며 계속하기가 사용하는 미리 컴파일된 헤더를 백그라운드에 로드하지 않으려면**

1. **디버그** 메뉴에서 **옵션 및 설정** 을 선택합니다.

2. **옵션** 대화 상자의 **디버깅** 노드에서 **편집하며 계속하기** 노드를 선택합니다.

3. **미리 컴파일 허용** 확인란 선택을 취소합니다.

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> IDL 특성 제한 사항
 편집하며 계속하기는 IDL(인터페이스 정의) 파일을 다시 생성하지 않습니다. 따라서 디버깅하는 동안 IDL 특성의 변경 내용이 반영되지 않습니다. IDL 특성을 변경한 결과를 확인하려면 디버깅을 중단하고 앱을 다시 빌드해야 합니다. 편집하며 계속하기는 IDL 특성이 변경되어도 오류나 경고를 생성하지 않습니다. 자세한 내용은 [IDL 특성](/cpp/windows/idl-attributes)을 참조하세요.

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> 문제 진단
 시나리오가 위에 언급된 조건에 맞지 않는 경우 다음 DWORD 레지스트리 값을 설정하여 자세한 정보를 수집할 수 있습니다.
 1. 개발자 명령 프롬프트를 엽니다.
 2. 다음 명령을 실행합니다.  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 디버그 세션을 시작할 때 이 값을 설정하면 편집하며 계속하기의 다양한 구성 요소가 **출력 창** > **디버그** 창에 자세한 정보 로깅을 생성합니다.

## <a name="see-also"></a>참조
- [편집하며 계속하기(C++)](../debugger/edit-and-continue-visual-cpp.md)
