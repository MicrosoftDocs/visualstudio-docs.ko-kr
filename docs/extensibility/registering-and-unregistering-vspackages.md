---
title: VSPackages | 등록 및 등록 취소 Microsoft Docs
description: 사용하는 특성 및 .pkgdef 파일을 포함하여 VSPackage 등록 및 등록 취소에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48067ed883a44870b3b753cb5e3d6943eca91ca5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900306"
---
# <a name="register-and-unregister-vspackages"></a>VSPackage 등록 및 등록 취소
특성을 사용하여 VSPackage를 등록하지만

## <a name="register-a-vspackage"></a>VSPackage 등록
 특성을 사용하여 관리되는 VSPackage 등록을 제어할 수 있습니다. 모든 등록 정보는 *.pkgdef* 파일에 포함되어 있습니다. 파일 기반 등록에 대한 자세한 내용은 [CreatePkgDef 유틸리티 를 참조하세요.](../extensibility/internals/createpkgdef-utility.md)

 다음 코드에서는 표준 등록 특성을 사용하여 VSPackage를 등록하는 방법을 보여 줍니다.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>확장 등록 취소
 다양한 VSPackage를 실험하고 실험적 인스턴스에서 제거하려는 경우 **Reset** 명령을 실행하기만 하면 됩니다. 컴퓨터의 시작 페이지에서 **Visual Studio 실험적 인스턴스** 다시 설정을 찾거나 명령줄에서 다음 명령을 실행합니다.

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Visual Studio 개발 인스턴스에 설치한 확장을 제거하려면 **도구** 확장 및  >  **업데이트로** 이동하여 확장을 찾은 다음 **제거를** 클릭합니다.

 어떤 이유로 이러한 메서드가 모두 확장을 제거하지 못하는 경우 다음과 같이 명령줄에서 VSPackage 어셈블리의 등록을 취소할 수 있습니다.

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>사용자 지정 등록 특성을 사용하여 확장 등록

경우에 따라 확장에 대한 새 등록 특성을 만들어야 할 수 있습니다. 등록 특성을 사용하여 새 레지스트리 키를 추가하거나 기존 키에 새 값을 추가할 수 있습니다. 새 특성은 에서 파생되어야 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 하며 및 메서드를 재정의해야 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 합니다.

### <a name="create-a-custom-attribute"></a>사용자 지정 특성 만들기

다음 코드는 새 등록 특성을 만드는 방법을 보여줍니다.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute>는 특성 클래스에서 특성이 관련된 프로그램 요소(클래스, 메서드 등), 두 번 이상 사용할 수 있는지 여부 및 상속 가능 여부를 지정하는 데 사용됩니다.

### <a name="create-a-registry-key"></a>레지스트리 키 만들기

다음 코드에서 사용자 지정 특성은 등록되는 VSPackage의 키 아래에 **사용자 지정** 하위 키를 만듭니다.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>기존 레지스트리 키 아래에 새 값 만들기

기존 키에 사용자 지정 값을 추가할 수 있습니다. 다음 코드는 VSPackage 등록 키에 새 값을 추가하는 방법을 보여줍니다.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>참조
- [VSPackages](../extensibility/internals/vspackages.md)
