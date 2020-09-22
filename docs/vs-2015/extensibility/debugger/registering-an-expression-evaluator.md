---
title: 식 계산기 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3595daa51fddf5c9c027d5643382918d85f83cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843389"
---
# <a name="registering-an-expression-evaluator"></a>식 계산기 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 식 계산기 (EE)는 Windows COM 환경 및 Visual Studio를 모두 사용 하 여 클래스 팩터리로 등록 해야 합니다. EE는 EE를 인스턴스화하는 엔터티에 따라 디버그 엔진 (DE) 주소 공간 또는 Visual Studio 주소 공간에 삽입 될 수 있도록 DLL로 구현 됩니다.  
  
## <a name="managed-code-expression-evaluator"></a>관리 코드 식 계산기  
 관리 코드 EE는 COM 환경을 사용 하 여 자신을 등록 하는 DLL 인 클래스 라이브러리로 구현 됩니다 .이 DLL은 일반적으로 VSIP 프로그램, **regpkg.exe**에 대 한 호출로 시작 됩니다. COM 환경에 대 한 레지스트리 키를 작성 하는 실제 프로세스는 자동으로 처리 됩니다.  
  
 주 클래스의 메서드는로 표시 되며,이 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 메서드는 DLL이 COM을 사용 하 여 등록 될 때 메서드가 호출 됨을 나타냅니다. 자주 호출 되는이 등록 메서드는 `RegisterClass` Visual Studio에 DLL을 등록 하는 작업을 수행 합니다. 해당 하는 `UnregisterClass` (로 표시 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 됨)는 `RegisterClass` DLL이 제거 될 때의 효과를 실행 취소 합니다.  
  
 비관리 코드로 작성 된 EE의 경우와 동일한 레지스트리 항목이 생성 됩니다. 유일한 차이점은 `SetEEMetric` 작업을 수행 하는 것과 같은 도우미 함수는 없다는 것입니다. 이 등록/등록 취소 프로세스의 예는 다음과 같습니다.  
  
### <a name="example"></a>예제  
 이 함수는 관리 코드 EE에서 Visual Studio를 사용 하 여 자체를 등록 및 등록 취소 하는 방법을 보여 줍니다.  
  
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
  
## <a name="unmanaged-code-expression-evaluator"></a>비관리 코드 식 계산기  
 EE DLL은 `DllRegisterServer` Visual Studio 뿐만 아니라 COM 환경에 자신을 등록 하는 함수를 구현 합니다.  
  
> [!NOTE]
> MyCEE 코드 샘플 레지스트리 코드는 dllentry 파일에서 찾을 수 있습니다 .이 파일은 VSIP 설치의 EnVSDK\MyCPkgs\MyCEE.에 있습니다.  
  
### <a name="dll-server-process"></a>DLL 서버 프로세스  
 EE를 등록할 때 DLL 서버는 다음과 같습니다.  
  
1. 클래스 팩터리 `CLSID` 를 일반적인 COM 규칙에 따라 등록 합니다.  
  
2. 도우미 함수를 호출 `SetEEMetric` 하 여 Visual Studio에 등록 하 고 다음 표에 표시 된 EE 메트릭을 사용 합니다. 아래에 `SetEEMetric` 지정 된 함수와 메트릭은 dbgmetric 라이브러리의 일부입니다. 자세한 내용은 [SDK 도우미를](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 참조 하세요.  
  
    |메트릭|Description|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` EE 클래스 팩터리|  
    |`metricName`|표시할 문자열의 EE 이름|  
    |`metricLanguage`|EE에서 평가 하도록 디자인 된 언어의 이름입니다.|  
    |`metricEngine`|`GUID`이 EE를 사용 하는 디버그 엔진 (DE)의입니다.|  
  
    > [!NOTE]
    > 는 `metricLanguage``GUID` 이름을 기준으로 언어를 식별 하지만 `guidLang` 언어를 선택 하는에 대 한 인수입니다 `SetEEMetric` . 컴파일러가 디버그 정보 파일을 생성 하는 경우 적절 한를 작성 해야 합니다 .이를 `guidLang` 위해 사용할 EE를 알 수 있습니다. DE는 일반적으로이 언어에 대 한 기호 공급자에 게 `GUID` 디버그 정보 파일에 저장 된 것을 요청 합니다.  
  
3. HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio x. Y 아래에 키를 만들어 Visual Studio에 등록 \\ *X.Y*합니다. 여기서 *X-y* 는 등록할 visual studio의 버전입니다.  
  
### <a name="example"></a>예제  
 이 함수는 비관리 코드 (c + +) EE에서 Visual Studio를 사용 하 여 등록 및 등록 취소 하는 방법을 보여 줍니다.  
  
```cpp#  
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
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
