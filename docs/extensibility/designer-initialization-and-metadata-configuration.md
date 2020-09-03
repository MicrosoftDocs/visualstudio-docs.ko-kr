---
title: 디자이너 초기화 및 메타 데이터 구성 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712220"
---
# <a name="designer-initialization-and-metadata-configuration"></a>디자이너 초기화 및 메타 데이터 구성

디자이너 또는 디자이너 구성 요소와 연결 된 메타 데이터 및 필터 특성을 조작 하면 응용 프로그램에서 다른 <xref:System.Type> 개체 (예: 데이터 구조, 클래스 또는 그래픽 엔터티)를 처리 하는 데 사용 되는 도구를 정의 하 고, 디자이너를 사용할 수 있을 때 디자이너를 지원 하도록 Visual STUDIO IDE를 구성 하는 방법을 정의할 수 있습니다 ( **도구 상자** 범주 또는 탭을 사용할 수 있음).

에서는 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSPackage를 통해 디자이너 또는 디자이너 구성 요소의 초기화와 해당 메타 데이터 조작을 편리 하 게 제어할 수 있는 몇 가지 메커니즘을 제공 합니다.

## <a name="initialize-metadata-and-configuration-information"></a>메타 데이터 및 구성 정보 초기화
 요청 시 로드 되기 때문에 디자이너를 인스턴스화 하기 전에 Visual Studio 환경에서 Vspackage를 로드 하지 않았을 수 있습니다. 따라서 Vspackage는 생성할 때 디자이너 또는 디자이너 구성 요소를 구성 하는 표준 메커니즘을 사용할 수 없습니다 .이는 이벤트를 처리 하기 위한 것입니다 <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> . 대신, VSPackage는 인터페이스의 인스턴스를 구현 하 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 고 자신을 등록 하 여 사용자 지정 (디자인 화면 확장 이라고 함)을 제공 합니다.

### <a name="customize-initialization"></a>초기화 사용자 지정

디자이너, 구성 요소 또는 디자이너 화면을 사용자 지정 하는 작업은 다음과 같습니다.

1. 디자이너 메타 데이터를 수정 하 고 특정에 액세스 하거나 변환 하는 방법을 효과적으로 변경 <xref:System.Type> 합니다.

    이는 일반적으로 또는 메커니즘을 통해 수행 됩니다 <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> .

    예를 들어 <xref:System.Windows.Forms> 기반 디자이너가 초기화 될 때 Visual Studio 환경에서는 <xref:System.Drawing.Design.UITypeEditor> 디자이너와 함께 사용 되는 개체에 대 한를 수정 하 여 <xref:System.Web.UI.WebControls.Image> 리소스 관리자를 사용 하 여 파일 시스템이 아닌 비트맵을 가져옵니다.

2. 예를 들어 이벤트를 구독 하거나 프로젝트 구성 정보를 가져오는 등 환경에를 통합 합니다. 인터페이스를 가져와 프로젝트 구성 정보를 얻고 이벤트를 구독할 수 있습니다 <xref:System.ComponentModel.Design.ITypeResolutionService> .

3. 디자이너에 클래스의 인스턴스를 적용 하 여 디자이너의 적용 가능성을 제한 하거나 적절 한 **도구 상자** 범주를 활성화 하 여 사용자 환경을 수정 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 합니다.

### <a name="designer-initialization-by-a-vspackage"></a>VSPackage 디자이너 초기화

VSPackage는 다음과 같은 방법으로 디자이너 초기화를 처리 해야 합니다.

1. 클래스를 구현 하는 개체 만들기 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>

   > [!NOTE]
   > 클래스는 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 클래스와 동일한 개체에서 구현 되어서는 안 됩니다 <xref:Microsoft.VisualStudio.Shell.Package> .

2. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>VSPackage의 디자이너 확장에 대 한 지원을 제공 하는를 구현 하는 클래스를 등록 합니다. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, 및의 인스턴스를 <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> VSPackage의 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 구현을 제공 하는 클래스에 적용 하 여 클래스를 등록 <xref:Microsoft.VisualStudio.Shell.Package> 합니다.

디자이너 또는 디자이너 구성 요소가 만들어질 때마다 Visual Studio 환경에서 다음을 수행 합니다.

- 등록 된 각 디자인 화면 확장 공급자에 액세스 합니다.

- 각 디자인 화면 확장 공급자의 개체의 인스턴스를 인스턴스화하고 초기화 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 합니다.

- 각 디자인 화면 확장 공급자의 메서드나 메서드를 적절 하 게 호출 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> 합니다.

<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>개체를 VSPackage의 멤버로 구현 하는 경우 다음을 이해 하는 것이 중요 합니다.

- Visual Studio 환경에서는 특정 공급자가 수정 하는 메타 데이터 나 기타 구성 설정에 대 한 제어를 제공 하지 않습니다 `DesignSurfaceExtension` . 두 개 이상의 공급자가 충돌 하 `DesignSurfaceExtension` 는 방식으로 동일한 디자이너 기능을 수정할 수 있으며 최종 수정이 결정적으로 발생 합니다. 수정 된 내용이 마지막으로 적용 되는 것은 아닙니다.

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>인스턴스 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 를 해당 구현에 적용 하 여 개체의 구현을 특정 디자이너로 명시적으로 제한할 수 있습니다. **도구 상자** 항목 필터링에 대 한 자세한 내용은 및을 참조 하십시오 <xref:System.ComponentModel.ToolboxItemFilterAttribute> <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>추가 메타 데이터 프로 비전

VSPackage는 디자인 타임이 아닌 디자이너 또는 디자이너 구성 요소의 구성을 변경할 수 있습니다.

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>클래스를 프로그래밍 방식으로 사용 하거나 디자이너를 제공 하는 VSPackage에 적용할 수 있습니다.

클래스의 인스턴스는 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 디자인 화면에 생성 된 구성 요소의 메타 데이터를 수정 하는 데 사용 됩니다. 예를 들어 개체에서 사용 하는 기본 속성 브라우저를 <xref:System.Windows.Forms.CommonDialog> 사용자 지정 속성 브라우저와 바꿀 수 있습니다.

의 VSPackage 구현에 적용 된 인스턴스에서 제공 하는 수정 사항은 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> <xref:Microsoft.VisualStudio.Shell.Package> 다음 두 범위 중 하나를 사용할 수 있습니다.

- 전역--지정 된 구성 요소의 모든 새 인스턴스에 대해

- 로컬-현재 VSPackage에서 제공 하는 디자인 화면에 생성 된 구성 요소의 인스턴스에만 관련 됩니다.

`IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> VSPackage의 구현에 적용 된 인스턴스의 속성은 <xref:Microsoft.VisualStudio.Shell.Package> 이 범위를 결정 합니다.

아래와 같이로 설정 된 개체의 속성을 사용 하 여의 구현에 특성을 적용 하면 <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> `true` 전체 Visual Studio 환경에 대해 브라우저가 변경 됩니다.

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

전역 플래그가로 설정 된 경우 `false` 메타 데이터 변경 내용은 현재 VSPackage에서 지 원하는 현재 디자이너에 대 한 로컬입니다.

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> 디자인 화면은 구성 요소 만들기만 지원 하므로 구성 요소에는 로컬 메타 데이터만 포함 될 수 있습니다. 위의 예제에서 개체의 속성과 같은 속성을 수정 하려고 했습니다 `Color` . `false`가 전역 플래그에 대해 전달 된 경우 `CustomBrowser` 디자이너에서 실제로의 인스턴스를 만들지 않으므로는 표시 되지 않습니다 `Color` . 전역 플래그를로 설정 하는 `false` 것은 컨트롤, 타이머 및 대화 상자와 같은 구성 요소에 유용 합니다.

## <a name="see-also"></a>추가 정보

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [디자인 타임 지원 확장](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
