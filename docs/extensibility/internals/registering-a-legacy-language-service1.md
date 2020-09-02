---
title: 레거시 언어 Service1 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0076eeee0ebcb0a80925efdde212097a3ec3e7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238883"
---
# <a name="registering-a-legacy-language-service-1"></a>레거시 언어 서비스 등록 1
MPF (관리 되는 패키지 프레임 워크)에서 언어 서비스는 VSPackage ( [vspackage](../../extensibility/internals/vspackages.md)참조)에 의해 제공 되 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 레지스트리 키와 항목을 추가 하 여에 등록 됩니다. 이 등록 프로세스는 부분적으로 설치 하는 동안 및 런타임에 부분적으로 수행 됩니다.

## <a name="register-the-language-service-by-using-attributes"></a>특성을 사용 하 여 언어 서비스 등록
 언어 서비스를 등록 하는 데 사용 되는 특성은 다음과 같습니다.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  이러한 특성은 아래에 설명 되어 있습니다.

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
 이 특성은 언어 서비스를 서비스로 등록 합니다.

### <a name="example"></a>예제

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideServiceAttribute(typeof(TestLanguageService),
                             ServiceName = "Test Language Service")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute
 이 특성은 언어 서비스를 특정 언어 서비스로 등록 합니다. 언어 서비스에서 제공 하는 기능을 지정 하는 옵션을 설정할 수 있습니다. 이 예제에서는 언어 서비스에서 제공할 수 있는 옵션의 하위 집합을 보여 줍니다. 언어 서비스 옵션의 전체 집합은을 참조 하십시오 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

### <a name="example"></a>예제

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),
                             "Test Language",
                             106,             // resource ID of localized language name
                             CodeSense = true,             // Supports IntelliSense
                             RequestStockColors = false,   // Supplies custom colors
                             EnableCommenting = true,      // Supports commenting out code
                             EnableAsyncCompletion = true  // Supports background parsing
                             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute
 이 특성은 언어 서비스를 파일 확장명에 연결 합니다. 이 확장명을 가진 파일이 로드 될 때마다 모든 프로젝트에서 언어 서비스가 시작 되어 파일 내용을 표시 하는 데 사용 됩니다.

### <a name="example"></a>예제

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),
                                       ".Testext")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute
 이 특성은 코드 확장 또는 코드 조각 템플릿을 가져오는 위치를 등록 합니다. 이 정보는 코드 조각 **브라우저** 및 코드 조각이 소스 파일에 삽입 될 때 편집기에서 사용 됩니다.

### <a name="example"></a>예제

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageCodeExpansionAttribute(
             typeof(TestLanguageService),
             "Test Language", // Name of language used as registry key.
             106,           // Resource ID of localized name of language service.
             "testlanguage",  // language key used in snippet templates.
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute
 이 특성은 **옵션** 대화 상자의 **텍스트 편집기** 범주에 표시 되는 속성 페이지를 등록 합니다. 각 페이지에 대해 이러한 특성 중 하나를 사용 하 여 언어 서비스에 대해 표시 합니다. 트리 구조에서 페이지를 구성 해야 하는 경우 추가 특성을 사용 하 여 트리의 각 노드를 정의 합니다.

### <a name="example"></a>예제
 이 예제에서는 두 개의 속성 페이지, **옵션** 및 **들여쓰기**와 두 번째 속성 페이지를 포함 하는 하나의 노드를 보여 줍니다.

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Options",      // Registry key name for property page
             "#242",         // Localized name of property page
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Advanced",     // Registry key name for node
             "#243",         // Localized name of node
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             @"Advanced\Indenting",     // Registry key name for property page
             "#244",         // Localized name of property page
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

## <a name="proffer-the-language-service-at-run-time"></a>런타임에 언어 서비스 Proffer
 언어 패키지가 로드 될 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 언어 서비스가 준비 되었음을 알려 주어 야 합니다. 이렇게 하려면 서비스를 proffering 합니다. 이 작업은 메서드에서 수행 됩니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> . 또한 유휴 기간 동안 언어 서비스를 호출 하는 타이머를 시작 해야 백그라운드 구문 분석을 수행할 수 있습니다. 클래스를 통해를 구현한 경우이 유휴 타이머는 문서 속성을 업데이트 하는 데도 사용 됩니다 <xref:Microsoft.VisualStudio.Package.DocumentProperties> . 타이머를 지원 하기 위해 패키지는 인터페이스를 구현 해야 합니다. <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> 메서드는 완전히 구현 되어야 하며 나머지 메서드는 기본값을 반환할 수 있습니다.

### <a name="example"></a>예제
 이 예제에서는 서비스를 proffering 하 고 유휴 타이머를 제공 하는 일반적인 방법을 보여 줍니다.

```csharp

using System;
using System.Runtime.InteropServices;
using System.ComponentModel.Design;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.OLE.Interop;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,
        AutoOutlining = true,
        EnableCommenting = true,
        MatchBraces = true,
        ShowMatchingBrace = true)]
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package

    public class TestLanguagePackage : Package, IOleComponent
    {
        private uint m_componentID;

        protected override void Initialize()
        {
            base.Initialize();  // required

            // Proffer the service.
            IServiceContainer serviceContainer = this as IServiceContainer;
            TestLanguageService langService      = new TestLanguageService();
            langService.SetSite(this);
            serviceContainer.AddService(typeof(TestLanguageService),
                                        langService,
                                        true);

            // Register a timer to call our language service during
            // idle periods.
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                       as IOleComponentManager;
            if (m_componentID == 0 && mgr != null)
            {
                OLECRINFO[] crinfo = new OLECRINFO[1];
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
                                              (uint)_OLECADVF.olecadvfRedrawOff |
                                              (uint)_OLECADVF.olecadvfWarningsOff;
                crinfo[0].uIdleTimeInterval = 1000;
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);
            }
        }

        protected override void Dispose(bool disposing)
        {
            if (m_componentID != 0)
            {
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                           as IOleComponentManager;
                if (mgr != null)
                {
                    int hr = mgr.FRevokeComponent(m_componentID);
                }
                m_componentID = 0;
            }

            base.Dispose(disposing);
        }

        #region IOleComponent Members

        public int FDoIdle(uint grfidlef)
        {
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;
            // Use typeof(TestLanguageService) because we need to
            // reference the GUID for our language service.
            LanguageService service = GetService(typeof(TestLanguageService))
                                      as LanguageService;
            if (service != null)
            {
                service.OnIdle(bPeriodic);
            }
            return 0;
        }

        public int FContinueMessageLoop(uint uReason,
                                        IntPtr pvLoopData,
                                        MSG[] pMsgPeeked)
        {
            return 1;
        }

        public int FPreTranslateMessage(MSG[] pMsg)
        {
            return 0;
        }

        public int FQueryTerminate(int fPromptUser)
        {
            return 1;
        }

        public int FReserved1(uint dwReserved,
                              uint message,
                              IntPtr wParam,
                              IntPtr lParam)
        {
            return 1;
        }

        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)
        {
            return IntPtr.Zero;
        }

        public void OnActivationChange(IOleComponent pic,
                                       int fSameComponent,
                                       OLECRINFO[] pcrinfo,
                                       int fHostIsActivating,
                                       OLECHOSTINFO[] pchostinfo,
                                       uint dwReserved)
        {
        }

        public void OnAppActivate(int fActive, uint dwOtherThreadID)
        {
        }

        public void OnEnterState(uint uStateID, int fEnter)
        {
        }

        public void OnLoseActivation()
        {
        }

        public void Terminate()
        {
        }

        #endregion
    }
}
```
