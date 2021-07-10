---
title: Visual Studio 확장 업데이트를 위한 ImageOptimizer 샘플
description: 예제를 따라가며 Visual Studio 확장이 Visual Studio 2022 Preview와 작동하도록 업데이트하는 방법을 알아봅니다.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 12bbc159884c16ea89849e5c97a4b87292f7089d
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602219"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer - Visual Studio 확장을 업데이트하는 단계별 방법

[!INCLUDE [preview-note](../includes/preview-note.md)]

이 가이드에서는 사례 연구를 통해 Image Optimizer 확장을 사용하여 Visual Studio 2019에 대한 지원을 유지하면서 Visual Studio 2022 지원을 추가하는 데 필요한 모든 단계를 보여 줍니다.  
이 가이드는 각 단계로 연결되는 git commit 링크가 포함된 상세 가이드입니다. [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46)에서 최종 PR을 살펴볼 수도 있습니다.

이 가이드에 마지막 부분에는 [추가 샘플](#other-samples)도 나와 있습니다.

## <a name="step-1---modernize-the-project"></a>1단계 - 프로젝트 현대화

See [프로젝트 현대화](update-visual-studio-extension.md#modernize-your-vsix-project)를 참조하세요.

[git commit e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

먼저 VSIX 및 단위 테스트 프로젝트를 프로젝트 속성 페이지의 .NET 4.7.2로 범프합니다.

   ![프레임워크 버전 범프](media/samples/framework-bump.png)

Image Optimizer는 오래된 사용자 지정 14.* 및 15.* 패키지를 참조하고 있는데 우리는 그 대신 필요한 모든 참조가 통합된 [`Microsoft.VisualStudio.Sdk` NuGet 패키지](https://www.nuget.org/packages/microsoft.visualstudio.sdk)를 설치하겠습니다.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

프로젝트가 성공적으로 빌드되고 몇 개의 스레드 경고가 표시됩니다. 경고는 `ctrl`과 `.`를 클릭하고 intellisense로 누락된 스레드 전환 줄을 추가하여 해결합니다.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>2단계 - 소스 코드를 공유 프로젝트로 리팩터링

[공유 프로젝트](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting)를 참조하세요.

Visual Studio 2022를 지원하려면 Visual Studio 2019 및 Visual Studio 2022 VSIX 프로젝트 간에 공유될 확장의 소스 코드를 포함할 새 공유 프로젝트를 추가해야 합니다.

1. 솔루션에 새 공유 프로젝트 추가

   [git commit abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![공유 프로젝트 추가](media/samples/add-shared-project.png)

1. VSIX 프로젝트에 공유 프로젝트에 대한 참조를 추가합니다.

   [git commit e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="공유 프로젝트 참조 추가" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. 다음을 **제외하고** 소스 코드 파일(cs, xaml, resx)을 새 공유 프로젝트로 이동합니다.
    - `source.extension.vsixmanifest`
    - 확장 메타데이터 파일(아이콘, 라이선스, 릴리스 정보 등)
    - VSCT 파일
    - 연결된 파일
    - VSIX에 포함해야 하는 외부 도구 또는 라이브러리

   [git commit f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![공유 프로젝트로 파일 이동](media/samples/move-to-shared-project.png)

1. 이제 모든 메타데이터, VSCT 파일, 연결된 파일, 외부 도구/라이브러리를 공유 위치로 이동하고 VSIX 프로젝트에 연결된 항목으로 다시 추가합니다. `source.extension.vsixmanifest`는 제거하지 마세요.

   [git commit 73ba920 - 파일 이동](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [git commit d5e36b2 - 외부 도구/라이브러리 추가](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. 이 프로젝트의 경우 확장 아이콘, VSCT 파일, 외부 도구를 새 폴더 `ImageOptimizer\Resources`로 이동해야 합니다. 해당 항목을 공유 폴더에 복사하고 VSIX 프로젝트에서 제거합니다.
   1. 항목을 다시 연결된 항목으로 추가하고 항목이 이미 연결된 항목인 경우 그대로 유지합니다(예: 라이선스).
   1. 각 항목을 선택하고 속성 도구 창을 확인하여 추가한 연결된 파일에서 빌드 작업 및 기타 속성이 올바르게 설정되었는지 확인합니다. 이 프로젝트에서는 다음을 설정해야 합니다.
       - `icon.png` 빌드 작업을 `Content`로 설정하고 VSIX에 포함을 `true`로 표시합니다.
       - `ImageOptimizer.vsct` 빌드 작업을 `VSCTComplile`로 설정하고 VSIX에 포함을 `false`로 표시합니다.
       - `Resources\Tools` 아래에 있는 파일의 모든 빌드 작업을 `Content`로 설정하고 VSIX에 포함을 `true`로 표시합니다.

           ![VSIX 프로젝트에 연결된 파일 추가](media/samples/add-linked-files.png)

       - `ImageOptimizer.cs`는 `ImageOptimizer.vsct`의 종속성입니다. 따라서 이 종속성을 csproj 파일에 수동으로 추가해야 합니다.

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - 속성 도구 창에서 특정 빌드 작업을 설정할 수 없는 경우 위에서처럼 필요에 따라 수동으로 csproj를 수정하고 빌드 작업을 설정할 수 있습니다.

1. 프로젝트를 빌드하여 변경 내용을 확인하고 오류/문제를 해결합니다. 자주 발생하는 문제는 [자주 묻는 질문](update-visual-studio-extension.md#q--a) 섹션을 참조하세요.

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>3단계 - Visual Studio 2022 VSIX 프로젝트 추가

[Visual Studio 2022 대상 추가](update-visual-studio-extension.md#add-a-visual-studio-2022-target)를 참조하세요.

1. 솔루션에 새 VSIX 프로젝트를 추가합니다.
1. `source.extension.vsixmanifest.`를 제외하고 새 프로젝트에서 추가 소스 코드를 제거합니다.

   ![새 VSIX 프로젝트 만들기](media/samples/visual-studio-2022-vsix-initial.png)

1. 공유 프로젝트에 참조를 추가합니다.

   [git commit dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="공유 프로젝트에 참조 추가" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Visual Studio 2019 VSIX 프로젝트의 연결된 파일을 추가하고 "빌드 작업" 속성과 "VSIX에 포함" 속성이 일치하는지 확인합니다. `source.extension.vsixmanifest` 파일도 복사합니다. 이 파일은 뒤에서 Visual Studio 2022를 지원하도록 수정할 것입니다.

   [git commit 98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![VSIX 프로젝트에 연결된 파일 추가](media/samples/visual-studio-2022-add-linked-files.png)

1. 빌드를 시도해 보면 `System.Windows.Forms`에 대한 참조가 누락되었음을 알 수 있습니다. 참조를 Visual Studio 2022 프로젝트에 추가하고 다시 빌드합니다.

   [git commit de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. `Microsoft.VisualStudio.SDK` 및 `Microsoft.VSSDK.BuildTools` 패키지 참조를 Visual Studio 2022 버전으로 업그레이드합니다.

   [git commit d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > 이는 이 가이드를 작성하는 시점의 최신 버전입니다. 해당 시점의 최신 버전을 받는 것이 좋습니다.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. `source.extension.vsixmanifest` 파일이 Visual Studio 2022 대상 지정을 반영하도록 편집합니다.

   [git commit 9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. `<InstallationTarget>` 태그가 Visual Studio 2022를 반영하도록 설정하고 amd64 페이로드를 명시합니다.

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Prerequisite가 Visual Studio 2022 이상만 포함하도록 수정합니다.

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

다 됐습니다!

이제 빌드하면 Visual Studio 2019 VSIX와 Visual Studio 2022 VSIX가 모두 생성됩니다.

## <a name="other-samples"></a>기타 샘플

- [ProPower 도구](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - 웹 브라우저를 피킹하여 선택한 클래스/개체에 대한 도움말 정보를 볼 수 있습니다.
  - FixMixedTabs
    - 문서를 검사하여 탭을 공백으로 또는 공백을 탭으로 바꿉니다.

## <a name="next-steps"></a>다음 단계

[시작부터 끝까지 안내하는 가이드](update-visual-studio-extension.md)를 참조하여 확장을 업데이트할 준비를 하세요.
