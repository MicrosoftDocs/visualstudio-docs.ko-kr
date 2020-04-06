---
title: VS패키지 의 리소스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705596"
---
# <a name="resources-in-vspackages"></a>VSPackage의 리소스
네이티브 위성 UI DLL, 관리되는 위성 DLL 또는 관리되는 VSPackage 자체에 지역화된 리소스를 포함할 수 있습니다.

 일부 리소스는 VSPackage에 포함할 수 없습니다. 다음과 같은 관리 형식을 포함할 수 있습니다.

- 문자열

- 패키지 로드 키(문자열이기도 합니다)

- 공구 창 아이콘

- 컴파일된 명령 테이블 출력(CTO) 파일

- CTO 비트맵

- 명령줄 도움말

- 대화 상자 데이터 정보

  관리되는 패키지의 리소스는 리소스 ID에 의해 선택됩니다. 예외는 CTMENU라는 이름을 지정해야 하는 CTO 파일입니다. CTO 파일은 리소스 테이블에 로 `byte[]`나타나야 합니다. 다른 모든 리소스 항목은 유형별로 식별됩니다.

  특성을 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 사용하여 관리되는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 리소스를 사용할 수 있음을 나타낼 수 있습니다.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  이러한 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 방식으로 설정하면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 예를 들어 를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>리소스를 검색할 때 관리되지 않는 위성 DLL을 무시해야 한다는 것을 나타냅니다. 동일한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 리소스 ID를 가진 두 개 이상의 리소스가 발생하는 경우 찾은 첫 번째 리소스를 사용합니다.

## <a name="example"></a>예제
 다음 예제는 도구 창 아이콘의 관리되는 표현입니다.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 다음 예제에서는 CTMENU라는 이름을 지정해야 하는 CTO 바이트 배열을 포함하는 방법을 보여 줍니다.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>구현 참고 사항
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 로딩이 지연될 수 있습니다. VSPackage에 CTO 파일을 포함하면 설치 중에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이러한 모든 VSPackage를 메모리에 로드해야 합니다. VSPackage에서 코드를 실행하지 않고 메타데이터를 검사하여 VSPackage에서 리소스를 추출할 수 있습니다. VSPackage는 현재 초기화되지 않으므로 성능 손실이 최소화됩니다.

 설치 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 후 VSPackage에서 리소스를 요청하는 경우 해당 패키지가 이미 로드되고 초기화될 가능성이 있으므로 성능 손실이 최소화됩니다.

## <a name="see-also"></a>참조
- [VSPackage 관리](../../extensibility/managing-vspackages.md)
- [MFC 애플리케이션의 지역화된 리소스: 위성 DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
