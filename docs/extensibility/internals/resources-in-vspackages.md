---
title: Vspackage의 리소스 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705596"
---
# <a name="resources-in-vspackages"></a>VSPackage의 리소스
지역화 된 리소스를 네이티브 위성 UI Dll, 관리 되는 위성 Dll 또는 관리 되는 VSPackage 자체에 포함할 수 있습니다.

 일부 리소스는 Vspackage에 포함할 수 없습니다. 다음 관리 되는 형식을 포함할 수 있습니다.

- 문자열

- 패키지 로드 키 (문자열 이기도)

- 도구 창 아이콘

- 컴파일된 명령 테이블 출력 (CTO) 파일

- CTO 비트맵

- 명령줄 도움말

- 대화 상자 데이터 정보

  관리 되는 패키지의 리소스는 리소스 ID로 선택 됩니다. 단, CTO 파일은 CTMENU로 이름을 지정 해야 합니다. CTO 파일은 리소스 테이블에으로 나타나야 합니다 `byte[]` . 다른 모든 리소스 항목은 유형으로 식별 됩니다.

  특성을 사용 하 여 관리 되는 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 리소스를 사용할 수 있음을 나타낼 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  이러한 방식으로를 설정 하면에서를 사용 하는 등의 방법으로 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 리소스를 검색할 때 관리 되지 않는 위성 dll을 무시 해야 함을 나타냅니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . 는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 동일한 리소스 ID를 가진 둘 이상의 리소스를 발견 하면 찾은 첫 번째 리소스를 사용 합니다.

## <a name="example"></a>예
 다음 예제는 도구 창 아이콘의 관리 되는 표현입니다.

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

 다음 예제에서는 CTMENU로 명명 되어야 하는 CTO 바이트 배열을 포함 하는 방법을 보여 줍니다.

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

## <a name="implementation-notes"></a>구현 노트
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 가능할 때마다 Vspackage의 로드를 지연 합니다. VSPackage에 CTO 파일을 포함 하면 설치 하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 동안 (병합 된 명령 테이블을 작성할 때) 모든 vspackage을 메모리에 로드 해야 합니다. VSPackage에서 코드를 실행 하지 않고 메타 데이터를 검사 하 여 VSPackage에서 리소스를 추출할 수 있습니다. VSPackage이 지금은 초기화 되지 않으므로 성능 손실이 최소화 됩니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 설치 후 VSPackage의 리소스를 요청 하면 해당 패키지가 이미 로드 되 고 초기화 될 수 있으므로 성능 손실은 최소화 됩니다.

## <a name="see-also"></a>추가 정보
- [VSPackage 관리](../../extensibility/managing-vspackages.md)
- [MFC 응용 프로그램의 지역화 된 리소스: 위성 Dll](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
