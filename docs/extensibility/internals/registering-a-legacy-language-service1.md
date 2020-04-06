---
title: 레거시 언어 서비스 등록1 | 마이크로 소프트 문서
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
ms.openlocfilehash: 91776382fff1818986049558c9d86e8fce4d0dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705898"
---
# <a name="registering-a-legacy-language-service"></a>레거시 언어 서비스 등록
MPF(관리되는 패키지 프레임워크)에서 언어 서비스는 VSPackage(VSPackages 참조)에서 제안되며 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 레지스트리 키와 항목을 추가하여 [등록됩니다.](../../extensibility/internals/vspackages.md) 이 등록 프로세스는 설치 중에 부분적으로, 부분적으로런 타임에 수행됩니다.

## <a name="register-the-language-service-by-using-attributes"></a>특성을 사용하여 언어 서비스 등록
 다음 특성은 언어 서비스를 등록하는 데 사용됩니다.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  이러한 특성은 아래에 설명되어 있습니다.

### <a name="provideserviceattribute"></a>서비스 속성 제공
 이 특성은 언어 서비스를 서비스로 등록합니다.

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

### <a name="providelanguageserviceattribute"></a>제공언어서비스속성
 이 특성은 언어 서비스를 구체적으로 언어 서비스로 등록합니다. 언어 서비스에서 제공하는 기능을 지정하는 옵션을 설정할 수 있습니다. 이 예제에서는 언어 서비스에서 제공할 수 있는 옵션의 하위 집합을 보여 주며 있습니다. 언어 서비스 옵션의 전체 집합은 을 참조하십시오. <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

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

### <a name="providelanguageextensionattribute"></a>제공언어확장특성
 이 특성은 언어 서비스를 파일 확장과 연결합니다. 해당 확장명이 있는 파일이 로드될 때마다 모든 프로젝트에서 언어 서비스가 시작되고 파일의 내용을 표시하는 데 사용됩니다.

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

### <a name="providelanguagecodeexpansionattribute"></a>제공언어코드확장특성
 이 특성은 코드 확장 또는 코드 조각 템플릿을 가져오는 위치를 등록합니다. 이 정보는 코드 **조각 브라우저와** 코드 조각이 소스 파일에 삽입될 때 편집기에서 사용됩니다.

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

### <a name="providelanguageeditoroptionpageattribute"></a>제공언어편집기옵션페이지속성
 이 특성은 **텍스트 편집기** 범주 아래의 **옵션** 대화 상자에 표시할 속성 페이지를 등록합니다. 언어 서비스에 표시할 각 페이지에 대해 이러한 특성 중 하나를 사용합니다. 트리 구조에서 페이지를 구성해야 하는 경우 추가 특성을 사용하여 트리의 각 노드를 정의합니다.

### <a name="example"></a>예제
 이 예제에서는 두 개의 속성 페이지인 **옵션** 및 **들여쓰기**및 두 번째 속성 페이지를 포함하는 노드 를 보여 주십습니다.

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

## <a name="proffer-the-language-service-at-run-time"></a>런타임에 언어 서비스 제공
 언어 패키지가 로드되면 언어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 서비스가 준비되었는 것을 알려야 합니다. 서비스를 제공 하 여이 작업을 수행 합니다. 이 작업은 메서드에서 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 수행됩니다. 또한 백그라운드 구문 분석이 수행될 수 있도록 유휴 기간 동안 언어 서비스를 호출하는 타이머를 시작해야 합니다. 이 유휴 타이머는 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 클래스를 통해 구현한 경우 문서 속성을 업데이트하는 데도 사용됩니다. 타이머를 지원하려면 패키지가 인터페이스를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> 구현해야 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> 합니다(메서드만 완전히 구현해야 하며 나머지 메서드는 기본값을 반환할 수 있음).

### <a name="example"></a>예제
 이 예제에서는 서비스를 제공하고 유휴 타이머를 제공하는 일반적인 방법을 보여 주며, 이 예제에서는 서비스를 제공합니다.

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
