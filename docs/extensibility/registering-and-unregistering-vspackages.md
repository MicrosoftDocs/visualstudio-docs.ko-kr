---
title: Vspackage 등록 및 등록 취소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f345bdbd3cf5858d495937c743b580abf5e3dd50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701588"
---
# <a name="register-and-unregister-vspackages"></a>Vspackage 등록 및 등록 취소
특성을 사용 하 여 VSPackage를 등록 하지만

## <a name="register-a-vspackage"></a>VSPackage 등록
 특성을 사용 하 여 관리 되는 Vspackage의 등록을 제어할 수 있습니다. 모든 등록 정보는 *.pkgdef* 파일에 포함 되어 있습니다. 파일 기반 등록에 대 한 자세한 내용은 [Createpkgdef 유틸리티](../extensibility/internals/createpkgdef-utility.md)를 참조 하세요.

 다음 코드에서는 표준 등록 특성을 사용 하 여 VSPackage를 등록 하는 방법을 보여 줍니다.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>확장 등록 취소
 다양 한 Vspackage를 실험 한 후 실험적 인스턴스에서 제거 하려는 경우 **Reset** 명령만 실행 하면 됩니다. 컴퓨터의 시작 페이지에서 **Visual Studio 실험적 인스턴스 다시 설정** 을 찾거나 명령줄에서 다음 명령을 실행 합니다.

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Visual Studio의 개발 인스턴스에 설치한 확장을 제거 하려면 **도구**  >  **확장 및 업데이트**로 이동 하 여 확장을 찾은 다음 **제거**를 클릭 합니다.

 어떤 이유로 든 확장을 제거 하는 데 이러한 메서드가 모두 성공 하지 못하는 경우 다음과 같이 명령줄에서 VSPackage 어셈블리를 등록 취소할 수 있습니다.

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>사용자 지정 등록 특성을 사용 하 여 확장 등록

특정 한 경우에는 확장에 대 한 새 등록 특성을 만들어야 할 수 있습니다. 등록 특성을 사용 하 여 새 레지스트리 키를 추가 하거나 기존 키에 새 값을 추가할 수 있습니다. 새 특성은에서 파생 되 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 고 및 메서드를 재정의 해야 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .

### <a name="create-a-custom-attribute"></a>사용자 지정 특성 만들기

다음 코드에서는 새 등록 특성을 만드는 방법을 보여 줍니다.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 는 특성 <xref:System.AttributeUsageAttribute> 클래스에서 특성을 사용 하는 프로그램 요소 (클래스, 메서드 등)를 지정 하는 데 사용 되며, 두 번 이상 사용할 수 있는지 여부 및 상속 될 수 있는지 여부를 지정 합니다.

### <a name="create-a-registry-key"></a>레지스트리 키 만들기

다음 코드에서 사용자 지정 특성은 등록 되는 VSPackage에 대 한 키 아래에 **사용자 지정** 하위 키를 만듭니다.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>기존 레지스트리 키 아래에 새 값을 만듭니다.

기존 키에 사용자 지정 값을 추가할 수 있습니다. 다음 코드에서는 VSPackage 등록 키에 새 값을 추가 하는 방법을 보여 줍니다.

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

## <a name="see-also"></a>추가 정보
- [VSPackages](../extensibility/internals/vspackages.md)
