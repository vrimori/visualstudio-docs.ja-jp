---
title: DPI Issues2 をアドレス指定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c85d867d042ea51023fc20259814a27b108e150
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875168"
---
# <a name="address-dpi-issues"></a>アドレス DPI 問題
「高解像度」画面には、デバイス数が増加が付属します。 通常、これらの画面には、200 を超えるピクセル/インチ (ppi) があります。 これらのコンピューター上のアプリケーションの操作は、コンテンツをデバイスの通常の表示までの距離にあるコンテンツを表示するためのニーズに合わせてスケール アップする必要があります。 2014 年の時点では、高密度ディスプレイの主なターゲットはモバイル コンピューティング デバイス (タブレットやクラムシェル ラップトップ、携帯電話です)。  
  
 Windows 8.1 以降では、これらのマシンとが表示されるマシンが高密度の両方に接続されているし、標準密度を同時に表示環境の使用を有効にするいくつかの機能が含まれています。  
  
- Windows は、「してテキストおよびその他のアイテム大きくまたは小さく」を使用してデバイスにコンテンツを拡大縮小することを許可できます (Windows XP 以降で使用可能) を設定します。  
  
- Windows 8.1 以降は、ピクセル密度の異なる表示間を移動すると、一貫性があるほとんどのアプリケーションのコンテンツを自動的にスケールします。 プライマリ ディスプレイは、高密度 (200% のスケーリング) とセカンダリの表示は、標準的な密度 (100%)、Windows を自動的にスケール アプリケーション ウィンドウの内容セカンダリ ディスプレイ (1 ピクセルの表示で表示された各 4 ピクセル、アプリケーションの場合)。  
  
- Windows は、ピクセル密度のスケールと距離の表示 (Windows 7 以降、OEM が構成可能な) を表示する右に設定されます。  
  
- Windows は 280 ppi (時点で、Windows 8.1 S14) を超える新しいデバイスによっては 250% にコンテンツを自動的にスケールできます。  
  
  Windows は、増加のピクセル数を活用するためにスケール アップ UI を扱うのことです。 アプリケーションを「システム DPI 認識」を宣言すること自体でこのシステムの選択します。 これを行わないアプリケーションには、システムによってをスケール アップします。 これは、結果、アプリケーション全体が一様に分布のピクセル拡大は「あいまい」のユーザー エクスペリエンス。 例:  
  
  ![DPI 問題あいまい](../extensibility/media/dpi-issues-fuzzy.png "DPI 問題あいまい")  
  
  Visual Studio オプトイン DPI スケーリングに対応して、そのため、「仮想化されません」  
  
  Windows (と Visual Studio) スケール係数は、システムによって設定の処理のさまざまな方法がありますが、いくつかの UI テクノロジを活用します。 例:  
  
- WPF では、(ユニット、ピクセル単位ではありません) は、デバイスに依存しない方法でコントロールを測定します。 WPF の UI は、現在 DPI 用に自動的にスケーリングされます。  
  
- UI フレームワークに関係なくすべてのテキストのサイズはポイント単位で表されますされ、そのため、DPI に依存しないと、システムによって処理されます。 Win32、WinForms、WPF でのテキストは既に、正しくスケーリングしてディスプレイ デバイスに描画した場合。  
  
- Win32/WinForms ダイアログと windows テキスト (たとえば、グリッド、flow、およびテーブル レイアウト パネルなど) を通じてによって調整されるレイアウトを有効にするための手段があります。 これらは、フォント サイズが増えたときはスケールされませんピクセルのハード コーディングされた場所の回避を有効にします。  
  
- アイコンは、システムによって提供またはシステム メトリック (たとえば、SM_CXICON および SM_CXSMICON) に基づいてリソースを既にスケール アップします。  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>古い Win32 (GDI、GDI +) および WinForms ベースの UI  
 WPF は、高 DPI 対応では既に、中に、Win32 GDI ベースのコードの多くはありませんで書き込まれている DPI 対応に注意してください。 Windows は、Api の DPI スケールを提供しています。 Win32 の問題の修正には、これら製品全体にわたる一貫した方法を使用する必要があります。 Visual Studio には、ヘルパーが提供されている機能を複製し、一貫性を維持し、製品を回避するためにクラス ライブラリ。  
  
## <a name="high-resolution-images"></a>高解像度のイメージ  
 このセクションでは、主に Visual Studio 2013 を拡張する開発者向けです。 Visual Studio 2015、Visual Studio に組み込まれているイメージのサービスを使用します。 多くのバージョンの Visual Studio のサポート/ターゲットする必要があるあり、したがって 2015年の イメージのサービスを使用してオプションではありません、以前のバージョンが存在しないためこともあります。 このセクションではまたです。  
  
## <a name="scaling-up-images-that-are-too-small"></a>スケール アップは小さすぎてイメージ  
 小さすぎるイメージをスケール アップし、GDI といくつかの一般的なメソッドを使用して WPF 上に描画します。 マネージ DPI ヘルパー クラスは、内部および外部の Visual Studio インテグレーター アイコン、ビットマップ、imagestrips、および imagelists をスケーリングするアドレスを使用できます。 Win32 ベースのネイティブ C と c++ ヘルパーを HICON、HBITMAP、HIMAGELIST、および VsUI::GdiplusImage を拡張するために利用できます。 通常、ビットマップのスケーリングでは、ヘルパー ライブラリへの参照を含めた後に 1 行の変更のみが必要です。 例:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Imagelist のスケーリングは、イメージ リストが、読み込み時に完了またはが実行時に追加されるかどうかによって異なります。 場合の読み込み時に完了すると、呼び出す`LogicalToDeviceUnits()`とイメージ リストでは、ビットマップ。 コードは、イメージ リストを作成する前に個々 のビットマップを読み込む必要があるの場合は、イメージ リストのイメージのサイズを調整することを確認してください。  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 ネイティブ コードは、次のように、イメージ リストを作成するときに、ディメンションをスケールできます。  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 ライブラリ内の関数は、サイズ変更のアルゴリズムを指定することを許可します。 ときに imagelists に格納するイメージをスケーリングは透過性、使用される背景色を指定することを確認または NearestNeighbor スケーリング (これは、125% と 150% にゆがみがにより) を使用します。  
  
 参照してください、 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN のドキュメント。  
  
 次の表では、スケール係数 dpi 対応するイメージをスケーリングする方法の例を示します。 オレンジ色で記載されているイメージは、(100 ~ 200 %dpi のスケール)、Visual Studio 2013 の時点で、ベスト プラクティスを示します。  
  
 ![DPI 問題 (スケーリング)](../extensibility/media/dpi-issues-scaling.png "DPI 問題 (スケーリング)")  
  
## <a name="layout-issues"></a>レイアウトの問題  
 絶対位置 (ピクセル単位) で具体的を使用してではなく、主に、スケール、UI には相互に関連したポイントを維持することによって、一般的なレイアウトの問題を回避できます。 例:  
  
- レイアウト]、[テキストの位置は、スケール アップしたイメージのアカウントに合わせて調整する必要があります。  
  
- グリッド内の列には、幅、スケール アップしたテキストに合わせて調整が必要です。  
  
- サイズのハード コーディングされたまたは要素の間にスペースは、スケール アップする必要があります。 テキスト分析コードのみに基づくサイズは、フォントを自動的にスケール アップされたため、通常は問題ありません。  
  
  ヘルパー関数では使用、 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> X と Y 軸上の拡張を許可するクラス。  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (関数が X でスケーリングを使用すると Y 軸)  
  
- int 領域 = DpiHelper.LogicalToDeviceUnitsX (10)。  
  
- int 高さ VsUI::DpiHelper::LogicalToDeviceUnitsY(5); を =  
  
  四角形、ポイント、およびサイズなどのオブジェクトの拡張を許可する LogicalToDeviceUnits オーバー ロードがあります。  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>スケールのイメージとレイアウトを DPIHelper ライブラリ/クラスを使用します。  
 Visual Studio の DPI のヘルパー ライブラリは、ネイティブおよびマネージ フォームで使用可能な他のアプリケーションで、Visual Studio shell の外部で使用できます。  
  
 ライブラリを使用するには、[拡張のサンプルを Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)および高 DPI_Images_Icons サンプルを複製します。  
  
 ソース ファイルに含める*VsUIDpiHelper.h*の静的関数を呼び出すと`VsUI::DpiHelper`クラス。  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  モジュール レベルまたはクラス レベルの静的変数には、ヘルパー関数を使用しません。 ライブラリがスレッドの同期も静的変数を使用し、順序初期化問題が発生する可能性があります。 これらの静的変数を非静的メンバー変数に変換またはいずれか (したがって、最初のアクセス、これらの構築を取得) を関数にそれらをラップします。  
  
 DPI のヘルパー関数は、Visual Studio 環境内で実行されるマネージ コードからアクセスします。  
  
-   使用中のプロジェクトでは、シェル MPF の最新バージョンを参照する必要があります。 例:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   プロジェクトへの参照に含まれることを確認**System.Windows.Forms**、 **PresentationCore**、および**PresentationUI**します。  
  
-   コードでは、使用、 **Microsoft.VisualStudio.PlatformUI** DpiHelper クラスの静的関数を名前空間を呼び出します。 (ポイント、サイズ、四角形、およびなど) のサポートされている型は、拡張機能を返す新しい関数オブジェクトを拡大縮小提供にがあります。 例:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>ズーム可能な UI での WPF イメージの許容量を処理します。  
 WPF では、ビットマップのサイズが変更に自動的に WPF では画像や、大規模なスクリーン ショットに適しては、見かけ上の許容量が導入されているために、メニュー項目のアイコンの適切な高品質双三次アルゴリズム (既定値) を使用して現在の DPI のズーム レベルの.  
  
 推奨事項:  
  
- ロゴ イメージとバナー アートワーク、既定の<xref:System.Windows.Media.BitmapScalingMode>サイズ モードを使用できます。  
  
- メニュー項目とアイコンのイメージの<xref:System.Windows.Media.BitmapScalingMode>が原因で他のゆがみ成果物 (200% で 300%) の許容を排除するときに使用する必要があります。  
  
- あいまい、色あせた UI は、大規模なズーム レベルを 100% (250% または 350% など) の倍数ではない、の結果双三次でリモコンの画像を拡大します。 最初の 100% (200% または 300% など) の最大の倍数に NearestNeighbor でイメージをスケーリングとそこから双三次によるスケールでより良い結果が取得されます。 特殊なケースを参照してください。 詳細情報のレベルの大規模な DPI の場合、WPF のイメージを prescaling します。  
  
  Microsoft.VisualStudio.PlatformUI 名前空間で DpiHelper クラス メンバーを提供する<xref:System.Windows.Media.BitmapScalingMode>をバインドに使用できます。 Visual Studio シェルは、ビットマップ スケーリング モード、製品内で一様に、DPI のスケール ファクターによって制御できるようになります。  
  
  XAML でこれを使用するには、次のように追加します。  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell は、既に最上位ウィンドウとダイアログ ボックスでこのプロパティを設定します。 Visual Studio で実行されている WPF ベースの UI には既に継承します。 場合は、設定は、特定の UI には伝達されません、/WPF XAML UI のルート要素で設定できます。 このような場所は、ポップアップ、Win32 の親を持つ要素を含めるし、Blend などのデザイナーのウィンドウの実行を処理します。  
  
 いくつかの UI は、WPF ベースのデザイナー (WPF デスクトップと Windows ストア)、Visual Studio テキスト エディターなど、システム設定の DPI ズーム レベルとは無関係にスケーリングできます。 このような場合は、DpiHelper.BitmapScalingMode を使用しない必要があります。 エディターでこの問題を解決するには、カスタム プロパティを作成した IDE チーム タイトル RenderOptions.BitmapScalingMode になります。 システムと、UI の組み合わせのズーム レベルに応じて HighQuality または NearestNeighbor にそのプロパティ値を設定します。  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>特殊なケース: prescaling WPF イメージの大規模な DPI レベル  
 100% (たとえば、250%、350% など) の倍数ではない非常に大きなズーム レベルの場合は、あいまい、色あせた ui 双三次結果を使用したことは考えませんイメージをスケーリングします。 錯覚のように鮮明なテキストの横のこれらのイメージのような印象がほぼです。 テキスト関連のフォーカスの内外の目に近い位置に、画像が表示されます。 この拡大されたサイズにスケーリングの結果は、最初、最大 100% (200% または 300% など) の倍数に NearestNeighbor でイメージをスケーリングと残りの部分 (さらに 50%) に双三次スケーリングによって向上できます。  
  
 次に、結果の違いの例の最初のイメージが拡大/縮小 200%]-> [100% 向上倍スケーリング アルゴリズムでは、250%]-> [および双三次 100% と同様に、2 つ目に 250%]-> [です。  
  
 ![DPI 問題スケーリングの例は二重](../extensibility/media/dpi-issues-double-scaling-example.png "DPI スケーリングの例を 2 つの問題")  
  
 この二重スケール、XAML マークアップを使用して、各イメージ要素を表示するために UI を有効にするためには、変更する必要があります。 次の例では、DpiHelper ライブラリと Shell.12/14 を使用して Visual Studio での WPF での二重スケールを使用する方法を示します。  
  
 手順 1: 200%、300%、NearestNeighbor を使用するようにイメージを prescale します。  
  
 バインディング、または XAML マークアップ拡張機能の適用にコンバーターを使用してイメージを prescale します。 例:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 イメージも構成される必要がある場合 (ほとんどすべてではない必要があります)、マークアップは、イメージと、事前のスケーリングのテーマを最初に異なるコンバーターを使用できます。 マークアップでは、いずれかを使用<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter>または<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>、目的の変換の出力によって異なります。  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 手順 2: 最終的なサイズが現在の DPI の正しいことを確認します。  
  
 WPF には、UIElement に設定 BitmapScalingMode プロパティを使用して、現在 DPI の UI は拡大縮小、ため、ソースに 2 ~ 3 倍よりも大きくなります prescaled イメージを使用して、イメージ コントロールする必要があります。 以下は、この特殊効果のカウンターの値に、いくつかの方法です。  
  
-   100% で、元のイメージのサイズがわかっている場合は、イメージ コントロールの正確なサイズを指定できます。 スケールする前に、UI のサイズが適用されるこれらのサイズが反映されます。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   元のイメージのサイズが不明である場合は、スケール ダウンが最終的なイメージ オブジェクトに、LayoutTransform を使用できます。 例:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>では、WebOC の HDPI サポートを有効にします。  
 既定では、WebOC コントロール (WPF、または IWebBrowser2 インターフェイスで WebBrowser コントロール) などは HDPI 検出とサポートを有効にしないでください。 結果は、高解像度のディスプレイに小さすぎる内容の表示と埋め込まれたコントロールになります。 次に、特定の web WebOC インスタンスで高 DPI のサポートを有効にする方法について説明します。  
  
 IDocHostUIHandler インターフェイスを実装 (上、MSDN の記事を参照してください、 [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 必要に応じて、ICustomDoc インターフェイスを実装 (上、MSDN の記事を参照してください、 [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 WebOC のドキュメントに IDocHostUIHandler を実装するクラスに関連付けます。 上記の ICustomDoc インターフェイスを実装した場合 WebOC のドキュメント プロパティは、使用するとすぐに、ICustomDoc にキャストし、IDocHostUIHandler を実装するクラスを渡して、SetUIHandler メソッドを呼び出します。  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 ICustomDoc インターフェイスを実装していないかどうかは、WebOC のドキュメントのプロパティが有効なとすぐには、IOleObject、および呼び出しにキャストする必要があります、 `SetClientSite` IDocHostUIHandler を実装するクラスを渡す方法です。 渡される受け取る DOCHOSTUIFLAG_DPI_AWARE フラグを設定して、`GetHostInfo`メソッドの呼び出し。  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 すべて HPDI をサポートするために、WebOC コントロールを取得する必要があります。  
  
## <a name="tips"></a>ヒント  
  
1.  WebOC コントロール上のドキュメント プロパティが変更された場合は、IDocHostUIHandler クラスを使用して、ドキュメントを再関連付けする必要があります。  
  
2.  上記が機能しない場合、変更、DPI フラグを取得していない WebOC に関する既知の問題があります。 この問題の修正の最も信頼性の高い方法では、WebOC、ズームの比率に 2 つの異なる値の 2 つの呼び出しを意味の光学ズームを切り替えます。 さらに、この回避策が必要な場合、移動の呼び出しごとに実行するために必要な場合があります。  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```
