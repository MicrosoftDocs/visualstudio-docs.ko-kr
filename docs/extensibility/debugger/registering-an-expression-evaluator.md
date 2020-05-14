---
title: 표현식 평가자 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713207"
---
# <a name="register-an-expression-evaluator"></a>식 계산기 등록
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 식 평가기(EE)는 Windows COM 환경과 Visual Studio를 모두 갖춘 클래스 팩터리로 등록해야 합니다. EE는 DLL로 설정되어 EE를 인스턴스화하는 엔터티에 따라 DE(디버그 엔진) 주소 공간 또는 Visual Studio 주소 공간에 삽입됩니다.

## <a name="managed-code-expression-evaluator"></a>관리되는 코드 식 평가기
 관리되는 코드 EE는 일반적으로 VSIP *프로그램인 regpkg.exe에*대한 호출로 시작하는 COM 환경에 자신을 등록하는 DLL인 클래스 라이브러리로 구현됩니다. COM 환경에 대한 레지스트리 키를 작성하는 실제 프로세스는 자동으로 처리됩니다.

 주 클래스의 메서드는 DLL이 COM에 등록될 때 메서드가 호출될 임을 나타내는 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>로 표시됩니다. 이 등록 방법(종종 호출)은 `RegisterClass`Visual Studio에 DLL을 등록하는 작업을 수행합니다. 해당(에 `UnregisterClass` <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>표시됨)은 DLL이 `RegisterClass` 제거된 경우의 효과를 취소합니다.
관리되지 않는 코드로 작성된 EE와 동일한 레지스트리 항목이 만들어집니다. 유일한 차이점은 당신을 위해 작업을 수행하는 것과 `SetEEMetric` 같은 도우미 기능이 없다는 것입니다. 다음은 등록 및 등록 취소 프로세스의 예입니다.

### <a name="example"></a>예제
 다음 함수는 관리되는 코드 EE가 Visual Studio에 자신을 등록하고 등록취소하는 방법을 보여 주며, 이 함수는 관리코드 EE가 자신을 등록하는 방법을 보여 주며,

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        #region Register and unregister.
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");
        private static string languageName = "MyC";
        private static string eeName = "MyC Expression Evaluator";

        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");

        /// <summary>
        /// Register the expression evaluator.
        /// Set "project properties/configuration properties/build/register for COM interop" to true.
        /// </summary>
         [ComRegisterFunctionAttribute]
        public static void RegisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator";

            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);
            if (rk == null)  return;

            rk = rk.CreateSubKey(guidMycLang.ToString("B"));
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));
            rk.SetValue("CLSID", t.GUID.ToString("B"));
            rk.SetValue("Language", languageName);
            rk.SetValue("Name", eeName);

            rk = rk.CreateSubKey("Engine");
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));
        }
        /// <summary>
        /// Unregister the expression evaluator.
        /// </summary>
         [ComUnregisterFunctionAttribute]
        public static void UnregisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator\"
                        + guidMycLang.ToString("B");
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);
            if (key != null)
            {
                key.Close();
                Registry.LocalMachine.DeleteSubKeyTree(s);
            }
        }
    }
}
```

## <a name="unmanaged-code-expression-evaluator"></a>관리되지 않는 코드 식 평가기
 EE DLL은 VISUAL `DllRegisterServer` Studio뿐만 아니라 COM 환경에 자신을 등록하는 기능을 구현합니다.

> [!NOTE]
> EnVSDK\MyCPkgs\MyCEE에서 VSIP 설치에 있는 파일 *dllentry.cpp에서*MyCEE 코드 샘플 레지스트리 코드를 찾을 수 있습니다.

### <a name="dll-server-process"></a>DLL 서버 프로세스
 EE를 등록할 때 DLL 서버는 다음을 수행합니다.

1. 일반 COM 규칙에 `CLSID` 따라 클래스 팩터리를 등록합니다.

2. 다음 표에 `SetEEMetric` 표시된 EE 메트릭을 Visual Studio에 등록하려면 도우미 함수를 호출합니다. 다음과 `SetEEMetric` 같이 지정된 함수 및 메트릭은 *dbgmetric.lib* 라이브러리의 일부입니다. 자세한 내용은 [DDK 도우미를](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 참조하십시오.

    |메트릭|설명|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`EE 급 공장의|
    |`metricName`|표시 가능한 문자열로 EE 이름|
    |`metricLanguage`|EE가 평가하도록 설계된 언어의 이름|
    |`metricEngine`|`GUID`이 EE와 함께 작동하는 디버그 엔진(DE)의|

    > [!NOTE]
    > 는 `metricLanguage``GUID` 이름으로 언어를 식별하지만 언어를 선택하는 `guidLang` `SetEEMetric` 인수입니다. 컴파일러가 디버그 정보 파일을 생성할 때 DE가 사용할 EE를 알 수 있도록 적절한 `guidLang` 파일을 작성해야 합니다. DE는 일반적으로 디버그 정보 `GUID`파일에 저장되는 이 언어에 대해 기호 공급자에게 요청합니다.

3. \\ *X.Y가* 등록할 Visual Studio 버전인 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y에서*키를 만들어 Visual Studio에 등록합니다.

### <a name="example"></a>예제
 다음 함수는 관리되지 않는 코드(C++) EE가 Visual Studio에 자신을 등록하고 등록 취소하는 방법을 보여 주며, 이 함수는 관리되지 않는 코드(C++)를 보여 주며, 이 함수는

```cpp
/*---------------------------------------------------------
  Registration
-----------------------------------------------------------*/
#ifndef LREGKEY_VISUALSTUDIOROOT
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"
#endif

static HRESULT RegisterMetric( bool registerIt )
{
    // check where we should register
    const ULONG cchBuffer = _MAX_PATH;
    WCHAR wszRegistrationRoot[cchBuffer];
    DWORD cchFreeBuffer = cchBuffer - 1;
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);
    wcscat(wszRegistrationRoot, L"\\");

    // this is Environment SDK specific
    // we check for  EnvSdk_RegKey environment variable to
    // determine where to register
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;
    DWORD cchEnvVarRead = GetEnvironmentVariableW(
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value
        /* DWORD   */ cchFreeBuffer);// size of buffer
    if (cchEnvVarRead >= cchFreeBuffer)
        return E_UNEXPECTED;
    // If the environment variable does not exist then we must use
    // LREGKEY_VISUALSTUDIOROOT which has the version number.
    if (0 == cchEnvVarRead)
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);

    if (registerIt)
    {
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricCLSID,
                    CLSID_MycEE,
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricName,
                    GetString(IDS_INFO_MYCDESCRIPTION),
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricLanguage, L"MyC",
                    wszRegistrationRoot);

        GUID engineGuids[2];
        engineGuids[0] = guidCOMPlusOnlyEng;
        engineGuids[1] = guidCOMPlusNativeEng;
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricEngine,
                    engineGuids,
                    2,
                    wszRegistrationRoot);
    }
    else
    {
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricCLSID,
                        wszRegistrationRoot);
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricName,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricLanguage,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricEngine,
                        wszRegistrationRoot );
    }

    return S_OK;
}
```

## <a name="see-also"></a>참조
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
