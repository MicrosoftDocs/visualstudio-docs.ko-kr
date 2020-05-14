---
title: 디자이너 초기화 및 메타데이터 구성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712220"
---
# <a name="designer-initialization-and-metadata-configuration"></a>디자이너 초기화 및 메타데이터 구성

디자이너 또는 디자이너 구성 요소와 연결된 메타데이터 및 필터 특성을 조작하면 응용 프로그램이 특정 디자이너가 <xref:System.Type> 다른 개체(예: 데이터 구조, 클래스 또는 그래픽 엔터티)를 처리하는 데 사용되는 도구, 디자이너를 사용할 수 있는 경우 및 디자이너를 지원하도록 구성된 Visual Studio IDE(예: **도구 상자** 범주 또는 탭사용 가능)를 정의하는 메커니즘을 제공합니다.

디자이너 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 또는 디자이너 구성 요소의 초기화를 제어하고 VSPackage에 의한 메타데이터의 조작을 용이하게 하기 위한 몇 가지 메커니즘을 제공합니다.

## <a name="initialize-metadata-and-configuration-information"></a>메타데이터 및 구성 정보 초기화
 요청 시 로드되므로 디자이너를 인스턴스화하기 전에 VISUAL Studio 환경에서 VSPackage가 로드되지 않았을 수 있습니다. 따라서 VSPackage는 이벤트를 처리하는 생성 시 디자이너 또는 디자이너 구성 요소를 구성하기 <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> 위한 표준 메커니즘을 사용할 수 없습니다. 대신 VSPackage인터페이스의 인스턴스를 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 구현하고 자체등록하여 디자인 표면 확장이라고 하는 사용자 지정을 제공합니다.

### <a name="customize-initialization"></a>초기화 사용자 지정

디자이너, 구성 요소 또는 디자이너 표면을 사용자 지정하려면 다음이 포함됩니다.

1. 디자이너 메타데이터를 수정하고 특정 <xref:System.Type> 데이터에 액세스하거나 변환하는 방법을 효과적으로 변경합니다.

    이것은 전형적으로 <xref:System.Drawing.Design.UITypeEditor> 또는 <xref:System.ComponentModel.TypeConverter> 메커니즘을 통해 수행된다.

    예를 <xref:System.Windows.Forms>들어-based 디자이너가 초기화되면 Visual Studio 환경은 <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> 디자이너와 함께 사용되는 개체에 대해 파일 시스템이 아닌 비트맵을 얻기 위해 리소스 관리자를 사용하도록 수정합니다.

2. 예를 들어 이벤트를 구독하거나 프로젝트 구성 정보를 가져오는 등 환경과 통합합니다. 인터페이스를 사용하여 프로젝트 구성 정보를 가져오고 <xref:System.ComponentModel.Design.ITypeResolutionService> 이벤트를 구독할 수 있습니다.

3. 적절한 **도구 상자** 범주를 활성화하거나 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 디자이너에 클래스의 인스턴스를 적용하여 디자이너의 적용 가능성을 제한하여 사용자 환경을 수정합니다.

### <a name="designer-initialization-by-a-vspackage"></a>VS패키지에 의한 디자이너 초기화

VSPackage는 디자이너 초기화를 다음과 같은 것으로 처리해야 합니다.

1. 클래스를 구현하는 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 개체만들기

   > [!NOTE]
   > 클래스는 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> <xref:Microsoft.VisualStudio.Shell.Package> 클래스와 동일한 개체에서 구현해서는 안 됩니다.

2. VSPackage의 디자이너 확장에 대 한 지원을 제공 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 으로 구현 하는 클래스를 등록 합니다. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>의 인스턴스를 <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>적용하 여 클래스를 등록 하 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 고 VSPackage의 <xref:Microsoft.VisualStudio.Shell.Package>구현을 제공 하는 클래스에 .

디자이너 또는 디자이너 구성 요소를 만들 때마다 Visual Studio 환경:

- 등록된 각 설계 표면 확장 공급자에 액세스합니다.

- 각 설계 표면 확장 공급자의 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 개체의 인스턴스를 인스턴스화하고 초기화합니다.

- 각 설계 표면 확장 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> 공급자의 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> 메서드 또는 메서드를 호출합니다(적절한 경우).

VSPackage의 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 멤버로 개체를 구현할 때 다음을 이해하는 것이 중요합니다.

- Visual Studio 환경은 특정 `DesignSurfaceExtension` 공급자가 수정하는 메타데이터 또는 기타 구성 설정을 제어하지 않습니다. 둘 이상의 `DesignSurfaceExtension` 공급자가 충돌하는 방식으로 동일한 디자이너 기능을 수정할 수 있으며 최종 수정은 최종 수정이 결정적입니다. 수정이 마지막으로 적용되는 것은 확정되지 않습니다.

- 해당 구현에 인스턴스를 적용하여 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 개체의 구현을 특정 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 디자이너로 명시적으로 제한할 수 있습니다. **도구 상자** 항목 필터링에 대한 자세한 <xref:System.ComponentModel.ToolboxItemFilterAttribute> <xref:System.ComponentModel.ToolboxItemFilterType>내용은 및 를 참조하십시오.

## <a name="additional-metadata-provisioning"></a>추가 메타데이터 프로비저닝

VSPackage는 디자인 타임이 아닌 디자이너 또는 디자이너 구성 요소의 구성을 변경할 수 있습니다.

클래스는 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 프로그래밍 방식으로 사용하거나 디자이너를 제공하는 VSPackage에 적용할 수 있습니다.

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 클래스의 인스턴스는 설계 표면에 작성된 구성 요소의 메타데이터를 수정하는 데 사용됩니다. 예를 들어 <xref:System.Windows.Forms.CommonDialog> 개체에서 사용하는 기본 속성 브라우저를 사용자 지정 속성 브라우저로 바꿀 수 있습니다.

VSPackage의 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 구현에 적용된 인스턴스에서 제공하는 수정 <xref:Microsoft.VisualStudio.Shell.Package> 사항은 다음 두 범위 중 하나를 가질 수 있습니다.

- 전역 -- 지정된 구성 요소의 모든 새 인스턴스에 대해

- 로컬 -- 현재 VSPackage에서 제공하는 설계 서피스에 작성된 구성요소의 인스턴스에만 관련된다.

VSPackage의 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 구현에 적용 된 인스턴스의 <xref:Microsoft.VisualStudio.Shell.Package> `IsGlobal` 속성이 이 범위를 결정 합니다.

다음과 <xref:Microsoft.VisualStudio.Shell.Package> 같이 개체의 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> 속성이 `true`다음과 같이 구현에 특성을 적용하면 전체 Visual Studio 환경에 대한 브라우저가 변경됩니다. <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

글로벌 플래그가 `false`로 설정된 경우 메타데이터 변경은 현재 VSPackage에서 지원하는 현재 디자이너에 로컬입니다.

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> 디자인 표면은 구성 요소 만들기만 지원하므로 구성 요소만 로컬 메타데이터를 가질 수 있습니다. 위의 예에서 개체의 속성과 같은 `Color` 속성을 수정하려고 했습니다. 전역 `false` 플래그에 대해 전달된 `CustomBrowser` 경우 디자이너가 실제로 `Color`의 인스턴스를 생성하지 않으므로 나타나지 않습니다. 전역 플래그를 `false` 설정하면 컨트롤, 타이머 및 대화 상자와 같은 구성 요소에 유용합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [설계 시간 지원 확장](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
