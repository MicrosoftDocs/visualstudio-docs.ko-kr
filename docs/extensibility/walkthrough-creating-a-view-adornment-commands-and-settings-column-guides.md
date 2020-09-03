---
title: 뷰 장식, 명령 및 설정 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c4be60f2285edb986d5ca7a1cf4a2202e03c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905040"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>연습: 뷰 장식, 명령 및 설정 만들기 (열 안내선)
명령 및 보기 효과를 사용 하 여 Visual Studio 텍스트/코드 편집기를 확장할 수 있습니다. 이 문서에서는 인기 있는 확장 기능인 열 안내선을 사용 하 여 시작 하는 방법을 보여 줍니다. 열 안내선은 텍스트 편집기의 뷰에서 코드를 특정 열 너비로 관리 하는 데 도움이 되는 시각적 밝은 선입니다. 특히 서식 지정 된 코드는 문서, 블로그 게시물 또는 버그 보고서에 포함 되는 샘플에 중요할 수 있습니다.

이 연습에서는 다음을 수행합니다.
- VSIX 프로젝트 만들기
- 편집기 뷰 장식 추가
- 설정 저장 및 가져오기에 대 한 지원 추가 (열 안내선 및 색을 그리는 위치)
- 명령 추가 (열 안내선 추가/제거, 색 변경)
- 편집 메뉴 및 텍스트 문서 상황에 맞는 메뉴에 명령 추가
- Visual Studio 명령 창에서 명령 호출에 대 한 지원 추가

  이 Visual Studio 갤러리[확장](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)을 사용 하 여 열 안내선 기능 버전을 사용해 볼 수 있습니다.

  > [!NOTE]
  > 이 연습에서는 Visual Studio 확장 템플릿에서 생성 된 몇 개의 파일에 많은 양의 코드를 붙여넣습니다. 그러나이 연습에서는 다른 확장 예제를 사용 하 여 GitHub에서 완료 된 솔루션을 참조 하 게 될 예정입니다. 완성 된 코드는 generictemplate 아이콘을 사용 하는 대신 실제 명령 아이콘이 있다는 차이가 있습니다.

## <a name="get-started"></a>시작하기
Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="set-up-the-solution"></a>솔루션 설정
먼저 VSIX 프로젝트를 만들고 편집기 뷰 장식을 추가한 다음 명령을 추가 하 여 명령을 소유 하는 VSPackage을 추가 합니다. 기본 아키텍처는 다음과 같습니다.
- 뷰 당 개체를 만드는 텍스트 뷰 생성 수신기가 있습니다 `ColumnGuideAdornment` . 이 개체는 필요에 따라 열 안내선을 변경, 업데이트 또는 다시 그리기 하는 뷰 변경 또는 설정에 대 한 이벤트를 수신 합니다.
- `GuidesSettingsManager`Visual Studio 설정 저장소에서 읽기 및 쓰기를 처리 하는가 있습니다. 또한 설정 관리자에는 사용자 명령 (열 추가, 열 제거, 색 변경)을 지 원하는 설정을 업데이트 하기 위한 작업이 포함 되어 있습니다.
- 사용자 명령이 있는 경우 필요한 VSIP 패키지가 있지만 commands 구현 개체를 초기화 하는 상용구 코드 일 뿐입니다.
- `ColumnGuideCommands`사용자 명령을 실행 하 고 *. vsct* 파일에 선언 된 명령에 대 한 명령 처리기를 후크 하는 개체가 있습니다.

  **VSIX**. **File &#124; New ...** 명령을 사용 하 여 프로젝트를 만듭니다. 왼쪽 탐색 창의 **c #** 에서 **확장성** 노드를 선택 하 고 오른쪽 창에서 **VSIX 프로젝트** 를 선택 합니다. 이름 **Columnguides** 를 입력 하 고 **확인** 을 선택 하 여 프로젝트를 만듭니다.

  **장식 보기**. 솔루션 탐색기의 프로젝트 노드에서 오른쪽 포인터 단추를 누릅니다. 새 **항목 &#124; 추가** ... 명령을 선택 하 여 새 뷰 장식 항목을 추가 합니다. 왼쪽 탐색 창에서 **확장성 &#124; 편집기** 를 선택 하 고 오른쪽 창에서 **편집기 뷰포트 장식** 을 선택 합니다. 이름 **Column 장식** 을 항목 이름으로 입력 하 고 **추가** 를 선택 하 여 추가 합니다.

  이 항목 템플릿에서는 프로젝트에 두 개의 파일 (참조 등)을 추가 하는 것을 볼 수 있습니다. **ColumnGuideAdornment.cs** 및 **ColumnGuideAdornmentTextViewCreationListener.cs**. 이 템플릿은 뷰에 자주색 사각형을 그립니다. 다음 섹션에서는 보기 생성 수신기에서 두 줄을 변경 하 고 **ColumnGuideAdornment.cs**의 내용을 바꿉니다.

  **명령**. **솔루션 탐색기**에서 프로젝트 노드의 오른쪽 포인터 단추를 누릅니다. 새 **항목 &#124; 추가** ... 명령을 선택 하 여 새 뷰 장식 항목을 추가 합니다. 왼쪽 탐색 창에서 **확장성 &#124; VSPackage** 를 선택 하 고 오른쪽 창에서 **사용자 지정 명령** 을 선택 합니다. 항목 이름으로 **ColumnGuideCommands** 이름을 입력 하 고 **추가**를 선택 합니다. 여러 참조 외에도 명령과 패키지를 추가 하면 **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**및 **ColumnGuideCommandsPackage**도 추가 됩니다. 다음 섹션에서는 첫 번째 및 마지막 파일의 내용을 대체 하 여 명령을 정의 하 고 구현 합니다.

## <a name="set-up-the-text-view-creation-listener"></a>텍스트 뷰 생성 수신기 설정
편집기에서 *ColumnGuideAdornmentTextViewCreationListener.cs* 를 엽니다. 이 코드는 Visual Studio에서 텍스트 뷰를 만들 때마다에 대 한 처리기를 구현 합니다. 뷰의 특성에 따라 처리기가 호출 되는 시기를 제어 하는 특성이 있습니다.

또한이 코드는 장식 계층을 선언 해야 합니다. 편집기는 뷰를 업데이트할 때 뷰 및 장식 요소를 가져오는에서 장식 계층을 가져옵니다. 특성을 사용 하 여 다른 사용자를 기준으로 계층의 순서를 선언할 수 있습니다. 다음 줄을 바꿉니다.

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

다음 두 줄을 사용 합니다.

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

바뀐 선은 장식 계층을 선언 하는 특성 그룹에 있습니다. 첫 번째 줄은 열 안내선이 나타나는 경우에만 변경 됩니다. 뷰의 텍스트가 텍스트의 앞뒤에 표시 되는 것을 의미 하는 "before" 선 그리기 두 번째 줄은 열 안내선 장식을 문서 개념에 맞는 텍스트 엔터티에 적용할 수 있는 것으로 선언 하지만 예를 들어 편집 가능한 텍스트에만 작동 하도록 장식을 선언할 수 있습니다. [언어 서비스 및 편집기 확장 지점의](../extensibility/language-service-and-editor-extension-points.md) 추가 정보가 있습니다.

## <a name="implement-the-settings-manager"></a>설정 관리자 구현
*GuidesSettingsManager.cs* 의 내용을 다음 코드로 바꿉니다 (아래 설명 참조).

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

이 코드의 대부분은 "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> , ..."와 같은 설정 형식을 만들고 구문 분석 합니다.  끝에 있는 정수는 열 안내선을 원하는 1부터 기반으로 하는 열입니다. 열 안내선 확장은 단일 설정 값 문자열에서 모든 설정을 캡처합니다.

코드를 강조 표시 하는 것이 좋습니다. 다음 코드 줄은 설정 저장소에 대 한 Visual Studio 관리 되는 래퍼를 가져옵니다. 대부분의 경우 Windows 레지스트리를 통해이를 추상화 하지만이 API는 저장소 메커니즘과는 독립적입니다.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Visual Studio 설정 저장소는 범주 식별자와 설정 식별자를 사용 하 여 모든 설정을 고유 하 게 식별 합니다.

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

를 범주 이름으로 사용할 필요는 없습니다 `"Text Editor"` . 원하는 항목을 선택할 수 있습니다.

처음 몇 가지 함수는 설정을 변경 하는 진입점입니다. 허용 되는 최대 안내선 수와 같은 높은 수준의 제약 조건을 확인 합니다.  그런 다음 `WriteSettings` 설정 문자열을 작성 하 고 속성을 설정 하는를 호출 `GuideLinesConfiguration` 합니다. 이 속성을 설정 하면 설정 값이 Visual Studio 설정 저장소에 저장 되 고 `SettingsChanged` 이벤트를 발생 하 여 `ColumnGuideAdornment` 각각 텍스트 뷰와 연결 된 모든 개체를 업데이트 합니다.

`CanAddGuideline`설정을 변경 하는 명령을 구현 하는 데 사용 되는와 같은 몇 가지 진입점 함수가 있습니다. Visual Studio는 메뉴를 표시 하는 경우 명령 구현을 쿼리하여 명령이 현재 활성화 되어 있는지, 해당 이름이 무엇 인지 등을 확인 합니다.  아래에서 명령 구현에 대 한 진입점을 연결 하는 방법을 확인할 수 있습니다. 명령에 대 한 자세한 내용은 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)을 참조 하세요.

## <a name="implement-the-columnguideadornment-class"></a>Column 장식 클래스 구현
`ColumnGuideAdornment`클래스는 장식을 포함할 수 있는 각 텍스트 뷰에 대해 인스턴스화됩니다. 이 클래스는 변경 또는 설정 변경에 대 한 이벤트를 수신 하 고 필요에 따라 열 가이드를 업데이트 하거나 다시 그리는 방법을 보여 줍니다.

*ColumnGuideAdornment.cs* 의 내용을 다음 코드로 바꿉니다 (아래 설명 참조).

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

이 클래스의 인스턴스는 연결 된 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 및 `Line` 뷰에 그려진 개체의 목록을 보유 합니다.

생성자 ( `ColumnGuideAdornmentTextViewCreationListener` Visual Studio에서 새 뷰를 만들 때에서 호출)는 열 안내선 `Line` 개체를 만듭니다.  또한 생성자는 `SettingsChanged` 이벤트 (에 정의 됨 `GuidesSettingsManager` ) 및 뷰 이벤트와에 대 한 처리기를 추가 합니다 `LayoutChanged` `Closed` .

`LayoutChanged`이 이벤트는 Visual Studio에서 뷰를 만드는 경우를 비롯 하 여 뷰의 여러 가지 변경 내용으로 인해 발생 합니다. `OnViewLayoutChanged`실행할 처리기를 호출 합니다 `AddGuidelinesToAdornmentLayer` . 의 코드는 `OnViewLayoutChanged` 글꼴 크기 변경, 보기 제본용, 가로 스크롤 등의 변경 내용에 따라 줄 위치를 업데이트 해야 하는지 여부를 결정 합니다. 의 코드를 통해 `UpdatePositions` 안내선은 텍스트의 줄에서 지정 된 문자 오프셋에 있는 텍스트의 열 바로 뒤 또는 문자 사이에 그려집니다.

설정이 변경 될 때마다 `SettingsChanged` 함수는 `Line` 새 설정에 관계 없이 모든 개체를 다시 만듭니다. 줄 위치를 설정한 후에는 코드에서 장식 계층의 모든 이전 개체를 제거 `Line` `ColumnGuideAdornment` 하 고 새 개체를 추가 합니다.

## <a name="define-the-commands-menus-and-menu-placements"></a>명령, 메뉴 및 메뉴 배치를 정의 합니다.
명령 및 메뉴를 선언 하 고, 다양 한 다른 메뉴에 명령 또는 메뉴 그룹을 배치 하 고, 명령 처리기를 연결 하는 것이 많은 경우가 있을 수 있습니다. 이 연습에서는이 확장에서 명령을 사용 하는 방법을 중점적으로 설명 하지만, 자세한 내용은 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)을 참조 하세요.

### <a name="introduction-to-the-code"></a>코드 소개
열 안내선 확장은 함께 포함 되는 명령 그룹 (열 추가, 열 제거, 줄 색 변경)을 선언 하 고 해당 그룹을 편집기의 상황에 맞는 메뉴의 하위 메뉴에 배치 하는 방법을 보여 줍니다.  열 안내선 확장은 또한 주 **편집** 메뉴에 명령을 추가 하지만 아래 일반적인 패턴으로 설명 된 대로 표시 되지 않습니다.

명령 구현에는 ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage 및 ColumnGuideCommands.cs의 세 가지 부분이 있습니다. 템플릿에 의해 생성 된 코드는 대화 상자를 구현 하는 **도구** 메뉴에 명령을 배치 합니다. 이는 간단 하므로 *vsct* 및 *ColumnGuideCommands.cs* 파일에서 구현 되는 방식을 확인할 수 있습니다. 아래 파일의 코드를 바꿉니다.

패키지 코드에는 Visual Studio에서 확장이 명령을 제공 하 고 명령을 넣을 위치를 찾는 데 필요한 상용구 선언이 포함 되어 있습니다. 패키지는 초기화 될 때 commands 구현 클래스를 인스턴스화합니다. 명령과 관련 된 패키지에 대 한 자세한 내용은 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)을 참조 하세요.

### <a name="a-common-commands-pattern"></a>일반 명령 패턴
열 안내선 확장의 명령은 Visual Studio에서 매우 일반적인 패턴의 예입니다. 그룹에 관련 명령을 입력 하 고,이 그룹을 주 메뉴에 배치 하는 것이 일반적으로 " `<CommandFlag>CommandWellOnly</CommandFlag>` "로 설정 되어 명령을 표시 하지 않도록 설정 합니다.  주 메뉴 (예: **편집**)에 명령을 배치 하면 **도구 옵션**에서 키 바인딩을 다시 할당할 때 명령을 찾는 데 유용한 이름을 사용할 수 있습니다 (예: 편집 **. addcolumnguide**). **명령 창**에서 명령을 호출 하는 경우 완료 하는 데에도 유용 합니다.

그런 다음 사용자가 명령을 사용할 것으로 요구 하는 상황에 맞는 메뉴 또는 하위 메뉴에 명령 그룹을 추가 합니다. Visual Studio는 `CommandWellOnly` 주 메뉴에 대해서만 표시 안 함 플래그로 처리 합니다. 상황에 맞는 메뉴 또는 하위 메뉴에 동일한 그룹의 명령을 두면 명령이 표시 됩니다.

일반적인 패턴의 일부분으로 열 안내선 확장은 단일 하위 메뉴를 포함 하는 두 번째 그룹을 만듭니다. 그러면 하위 메뉴에 4 열 안내선 명령이 있는 첫 번째 그룹이 포함 됩니다. 하위 메뉴를 포함 하는 두 번째 그룹은 해당 상황에 맞는 메뉴에 하위 메뉴를 배치 하는 다양 한 상황에 맞는 메뉴에 배치 하는 재사용 가능한 자산입니다.

### <a name="the-vsct-file"></a>. Vsct 파일
*. Vsct* 파일은 아이콘과 함께 명령과 함께 이동 하는 위치를 선언 합니다. *. Vsct* 파일의 내용을 다음 코드로 바꿉니다 (아래 설명 참조).

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**Guid**. Visual Studio에서 명령 처리기를 찾고 호출 하려면 *ColumnGuideCommandsPackage.cs* 파일 (프로젝트 항목 템플릿에서 생성 됨)에 선언 된 패키지 guid가 *. vsct* 파일 (위에서 복사 됨)에 선언 된 패키지 guid와 일치 하는지 확인 해야 합니다. 이 샘플 코드를 다시 사용 하는 경우이 코드를 복사 했을 수 있는 다른 사용자와 충돌 하지 않도록 다른 GUID가 있는지 확인 해야 합니다.

*ColumnGuideCommandsPackage.cs* 에서 다음 줄을 찾고 따옴표 사이에서 GUID를 복사 합니다.

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

그런 다음 선언에 다음 줄을 포함 하도록 GUID를 *vsct* 파일에 붙여넣습니다. `Symbols`

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

명령 집합 및 비트맵 이미지 파일의 Guid는 확장에 대해서만 고유 해야 합니다.

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

그러나이 연습에서는 명령 집합 및 비트맵 이미지 Guid를 변경 하 여 코드를 사용할 필요가 없습니다. 명령 집합 GUID는 *ColumnGuideCommands.cs* 파일의 선언과 일치 해야 하지만 해당 파일의 내용만 바꿉니다. 따라서 Guid가 일치 합니다.

*. Vsct* 파일의 다른 guid는 열 안내선 명령이 추가 되는 기존 메뉴를 식별 하므로 변경 되지 않습니다.

**파일 섹션**. *. Vsct* 에는 명령, 배치 및 기호 라는 세 개의 외부 섹션이 있습니다. 명령 섹션에서는 명령 그룹, 메뉴, 단추 또는 메뉴 항목 및 아이콘에 대 한 비트맵을 정의 합니다. 배치 섹션은 그룹이 메뉴 또는 기존 메뉴에 추가 위치로 이동 하는 위치를 선언 합니다. 기호 섹션 *은 .vvsct 파일의* 다른 곳에서 사용 되는 식별자를 선언 합니다 .이 경우에는 모든 위치에서 guid와 16 진수를 사용 하는 것 보다 더 읽기 쉬운 *.*

**명령 섹션, 그룹 정의**. 명령 섹션에서는 먼저 명령 그룹을 정의 합니다. 명령 그룹은 그룹을 구분 하는 작은 회색 줄이 있는 메뉴에 표시 되는 명령입니다. 또한이 예제와 같이 그룹에 전체 하위 메뉴가 채워질 수 있으며,이 경우에는 회색으로 구분 된 줄이 표시 되지 않습니다. *. Vsct* 파일은 두 개의 그룹을 선언 합니다 .이 두 그룹은 `GuidesMenuItemsGroup` `IDM_VS_MENU_EDIT` (주 **편집** 메뉴)의 부모로,는 `GuidesContextMenuGroup` `IDM_VS_CTXT_CODEWIN` (코드 편집기의 상황에 맞는 메뉴)입니다.

두 번째 그룹 선언에는 `0x0600` 우선 순위가 있습니다.

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

이 개념은 하위 메뉴 그룹을 추가 하는 상황에 맞는 메뉴의 끝에 열 안내선 하위 메뉴를 배치 하는 것입니다. 그러나 가장 잘 알고 있는 것으로 가정 하 고 우선 순위를 사용 하 여 하위 메뉴가 항상 마지막으로 적용 되도록 하는 것은 아닙니다 `0xFFFF` . 숫자를 사용 하 여 해당 하위 메뉴가 배치 된 상황에 맞는 메뉴에 있는 위치를 확인 해야 합니다. 이 경우는 `0x0600` 볼 수 있는 한 메뉴의 끝에 배치 하기에 충분 하지만, 원하는 경우 다른 사람이 확장을 디자인 하 여 열 안내선 확장 보다 낮게 유지 하는 공간을 확보 합니다.

**명령 섹션, 메뉴 정의**. 그런 다음 명령 섹션은의 부모로 하위 메뉴 `GuidesSubMenu` 를 정의 합니다 `GuidesContextMenuGroup` . 는 `GuidesContextMenuGroup` 관련 된 모든 상황에 맞는 메뉴에 추가 하는 그룹입니다. 배치 섹션에서 코드는이 하위 메뉴에 4 열 안내선 명령이 있는 그룹을 배치 합니다.

**명령 섹션, 단추 정의**. 그런 다음 명령 섹션에서는 네 열로 된 안내선 명령인 메뉴 항목이 나 단추를 정의 합니다. `CommandWellOnly`위에서 설명한 것 처럼, 주 메뉴에 배치 하면 명령이 표시 되지 않습니다. 메뉴 항목 단추 선언 (가이드 추가 및 가이드 제거)에는 플래그도 있습니다 `AllowParams` .

```xml
<CommandFlag>AllowParams</CommandFlag>
```

이 플래그를 사용 하면 Visual Studio에서 명령 처리기를 호출할 때 주 메뉴 배치를 사용 하 여 인수를 받는 명령이 가능 합니다.  사용자가 명령 창에서 명령을 실행 하는 경우 인수는 이벤트 인수의 명령 처리기에 전달 됩니다.

**명령 섹션, 비트맵 정의**. 마지막으로 명령 섹션은 명령에 사용 되는 비트맵 또는 아이콘을 선언 합니다. 이 섹션은 프로젝트 리소스를 식별 하 고 사용 된 아이콘의 인덱스 (1부터 사용)를 나열 하는 간단한 선언입니다. *. Vsct* 파일의 기호 섹션은 인덱스로 사용 되는 식별자의 값을 선언 합니다. 이 연습에서는 프로젝트에 추가 된 사용자 지정 명령 항목 템플릿과 함께 제공 된 비트맵 스트립을 사용 합니다.

배치 **섹션**. 명령 섹션 뒤에 배치 섹션이 있습니다. 첫 번째는 코드에서 위에 설명 된 첫 번째 그룹을 추가 하 여 명령이 표시 되는 하위 메뉴에 4 열 안내선 명령을 포함 하는 것입니다.

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

다른 모든 위치에는를 포함 하는를 `GuidesContextMenuGroup` `GuidesSubMenu` 다른 편집기 상황에 맞는 메뉴에 추가 합니다. 로 선언 된 코드는 `GuidesContextMenuGroup` 코드 편집기의 상황에 맞는 메뉴의 부모로 선언 됩니다. 따라서 코드 편집기의 상황에 맞는 메뉴에 대 한 배치가 표시 되지 않습니다.

**기호 섹션**. 위에서 설명한 것 처럼 기호 섹션은 *vsct* 파일의 다른 곳에서 사용 되는 식별자를 선언 합니다 .이 경우에는 모든 위치에서 guid와 16 진수를 사용 하는 것 보다 *vsct* 코드를 더 읽기 쉽게 만듭니다. 이 섹션에서 중요 한 점은 패키지 GUID가 package 클래스의 선언과 일치 해야 한다는 것입니다. 명령 집합 GUID는 명령 구현 클래스의 선언과 일치 해야 합니다.

## <a name="implement-the-commands"></a>명령 구현
*ColumnGuideCommands.cs* 파일은 명령을 구현 하 고 처리기를 후크합니다. Visual Studio에서 패키지를 로드 하 고 초기화 하면 패키지에서 `Initialize` commands 구현 클래스에 대해를 호출 합니다. 명령 초기화는 단순히 클래스를 인스턴스화하고 생성자는 모든 명령 처리기를 후크합니다.

*ColumnGuideCommands.cs* 파일의 내용을 다음 코드로 바꿉니다 (아래 설명 참조).

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**참조를 수정**합니다. 이 시점에서 참조가 누락 되었습니다. 솔루션 탐색기의 참조 노드에서 오른쪽 포인터 단추를 누릅니다. **추가 ...** 명령을 선택 합니다. **참조 추가** 대화 상자의 오른쪽 위 모서리에 검색 상자가 있습니다. "편집기" (큰따옴표 제외)를 입력 합니다. 항목을 선택 하는 것이 아니라 항목의 왼쪽에 있는 상자를 선택 해야 합니다. **VisualStudio** 항목을 선택 하 고 **확인** 을 선택 하 여 참조를 추가 합니다.

**초기화**.  Package 클래스는를 초기화할 때 `Initialize` commands 구현 클래스에서를 호출 합니다. 초기화는 클래스 `ColumnGuideCommands` 를 인스턴스화하고 클래스 인스턴스 및 패키지 참조를 클래스 멤버에 저장 합니다.

클래스 생성자에서 명령 처리기 후크 중 하나를 살펴보겠습니다.

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

을 만듭니다 `OleMenuCommand` . Visual Studio는 Microsoft Office 명령 시스템을 사용 합니다. 을 인스턴스화할 때 키 인수는 `OleMenuCommand` command ()를 구현 하는 함수입니다 `AddColumnGuideExecuted` . Visual Studio에서 명령 ( `AddColumnGuideBeforeQueryStatus` ) 및 명령 ID를 사용 하 여 메뉴를 표시 하는 경우 호출할 함수입니다. Visual studio는 메뉴에 명령을 표시 하기 전에 쿼리 상태 함수를 호출 하 여 메뉴의 특정 표시 (예: 선택 영역이 없는 경우 **복사** 비활성화)에 대해 명령이 표시 되지 않거나 회색으로 표시 되도록 하거나, 아이콘을 변경 하거나, 다른 항목을 제거 하는 등의 작업을 수행 하는 등의 방법으로 해당 이름을 변경 합니다. 명령 ID는 *. vsct* 파일에 선언 된 명령 id와 일치 해야 합니다. 명령 집합 및 열 안내선 추가 명령에 대 한 문자열은 *. vsct* 파일과 *ColumnGuideCommands.cs*사이에 일치 해야 합니다.

다음 줄은 명령 창을 통해 사용자가 명령을 호출 하는 경우에 대 한 지원을 제공 합니다 (아래 설명 참조).

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **쿼리 상태**. 쿼리 상태 함수는 `AddColumnGuideBeforeQueryStatus` `RemoveColumnGuideBeforeQueryStatus` 일부 설정 (예: 최대 안내선 수 또는 최대 열 수)을 확인 하 고 제거할 열 가이드가 있는 경우이를 확인 합니다. 조건이 올바른 경우 명령을 사용 하도록 설정 합니다.  쿼리 상태 함수는 Visual Studio가 메뉴를 표시 하 고 메뉴의 각 명령에 대해 실행할 때마다 실행 되므로 효율적 이어야 합니다.

 **Addcolumn가이드에서 함수를 실행**했습니다. 가이드를 추가 하는 흥미로운 부분은 현재 편집기 보기와 캐럿 위치를 파악 하는 것입니다.  첫째,이 함수는 `GetApplicableColumn` 명령 처리기의 이벤트 인수에 사용자 제공 인수가 있는지 확인 하는를 호출 하 고, 없는 경우 함수는 편집기의 뷰를 확인 합니다.

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` 코드 보기를 약간 자세히 살펴보겠습니다 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .  , 및을 통해 추적 하는 경우이 `GetActiveTextView` `GetActiveView` `GetTextViewFromVsTextView` 작업을 수행 하는 방법을 확인할 수 있습니다. 다음 코드는 현재 선택 영역에서 시작 하 고, 선택의 프레임을 가져온 다음, 프레임의 DocView를으로 가져오고, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> IVsTextView에서을 가져오고, 뷰 호스트를 가져오고, 마지막으로 IWpfTextView 하는 관련 코드를 추출 합니다.

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

IWpfTextView가 있으면 캐럿이 있는 열을 가져올 수 있습니다.

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

사용자가 클릭 한 위치에 현재 열을 포함 하는 코드는 설정 관리자에 대해를 호출 하 여 열을 추가 하거나 제거 합니다. 설정 관리자는 모든 개체가 수신 대기 하는 이벤트를 발생 시킵니다 `ColumnGuideAdornment` . 이벤트가 발생 하면 이러한 개체는 연결 된 텍스트 뷰를 새 열 안내선 설정으로 업데이트 합니다.

## <a name="invoke-command-from-the-command-window"></a>명령 창에서 명령 호출
열 안내선 샘플을 사용 하면 사용자가 명령 창에서 두 개의 명령을 확장성 형식으로 호출할 수 있습니다. **다른 창 &#124; &#124; 보기** 명령을 사용 하는 경우 명령 창을 볼 수 있습니다. "Edit."를 입력 하 고 명령 이름 완성을 사용 하 고 인수 120을 제공 하 여 명령 창과 상호 작용할 수 있습니다. 예를 들면 다음과 같습니다.

```csharp
> Edit.AddColumnGuide 120
>
```

이 동작을 사용 하도록 설정 하는 샘플 부분은 *. vsct* 파일 선언, `ColumnGuideCommands` 명령 처리기를 후크 할 때의 클래스 생성자 및 이벤트 인수를 확인 하는 명령 처리기 구현에 있습니다.

`<CommandFlag>CommandWellOnly</CommandFlag>` **편집** 메뉴 UI에 명령이 표시 되지 않지만 *vsct* 파일에서 ""를 표시 하 고 **편집** 주 메뉴에 배치 하는 것도 가능 합니다. 주 **편집** 메뉴에 있으면 **편집. addcolumnguide**와 같은 이름이 제공 됩니다. 명령 그룹 선언은 그룹을 **편집** 메뉴에 직접 배치 하는 명령 그룹 선언입니다.

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

나중에 단추 섹션에서 주 메뉴에 표시 되지 않는 명령을 선언 하 `CommandWellOnly` 고로 선언 `AllowParams` 했습니다.

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

허용 된 매개 변수에 대 한 설명을 제공 하는 클래스 생성자에서 명령 처리기 후크 코드를 확인 `ColumnGuideCommands` 했습니다.

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

`GetApplicableColumn` `OleMenuCmdEventArgs` 현재 열에 대해 편집기의 뷰를 확인 하기 전에 함수에서 값을 확인 하는 것을 확인 했습니다.

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>확장 시도
이제 **F5** 키를 눌러 열 안내선 확장을 실행할 수 있습니다. 텍스트 파일을 열고 편집기의 상황에 맞는 메뉴를 사용 하 여 안내선을 추가, 제거 및 색을 변경 합니다. 텍스트 (공백 없음)를 클릭 하 여 열 안내선을 추가 하거나 편집기가 해당 줄의 마지막 열에 추가 합니다. 명령 창을 사용 하 고 인수를 사용 하 여 명령을 호출 하는 경우 아무 곳에 나 열 안내선을 추가할 수 있습니다.

다른 명령 배치를 시도 하 고, 이름을 변경 하 고, 아이콘을 변경 하 고, Visual Studio에서 메뉴의 최신 코드를 표시 하는 데 문제가 있는 경우 디버깅 중인 실험적 하이브를 다시 설정할 수 있습니다. **Windows 시작 메뉴** 를 열고 "다시 설정"을 입력 합니다. 명령을 찾아 실행 하 고 **다음 Visual Studio 실험적 인스턴스를 다시 설정**합니다. 이 명령은 모든 확장 구성 요소의 실험적 레지스트리 하이브를 정리 합니다. 구성 요소에서 설정을 정리 하지 않으므로, Visual Studio의 실험적 hive를 종료할 때 있던 모든 가이드는 코드에서 다음 시작 시 설정 저장소를 읽을 때에도 있습니다.

## <a name="finished-code-project"></a>완성 된 코드 프로젝트
Visual Studio 확장성 샘플의 GitHub 프로젝트가 곧 표시 되 고 완료 된 프로젝트가 표시 됩니다. 이 문서는 발생 하는 경우를 가리키도록 업데이트 됩니다. 완성 된 샘플 프로젝트는 다른 guid를 포함할 수 있으며 명령 아이콘에 대해 다른 비트맵 스트립을 갖습니다.

이 Visual Studio 갤러리[확장](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)을 사용 하 여 열 안내선 기능 버전을 사용해 볼 수 있습니다.

## <a name="see-also"></a>추가 정보
- [편집기 내부](../extensibility/inside-the-editor.md)
- [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)
- [언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [메뉴에 하위 메뉴 추가](../extensibility/adding-a-submenu-to-a-menu.md)
- [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)
