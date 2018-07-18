---
title: DPI Issues2 をアドレス指定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc0801d3fb43188ac3371ed7e5e7394b0e3aad72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108444"
---
# <a name="addressing-dpi-issues"></a>DPI 問題に対処して
「高解像度」画面には、デバイス数が増加が付属します。 これらの画面には、通常、200 を超えるピクセル/インチ (ppi) があります。 これらのコンピューター上のアプリケーションの操作には、デバイスの通常の表示距離にあるコンテンツを表示するためのニーズに合わせてスケール アップするコンテンツが必要です。 2014 年の時点で、プライマリ ターゲット高密度ディスプレイではモバイル コンピューティング デバイス (タブレット、クラムシェル ラップトップ、携帯電話) です。  
  
 Windows 8.1 以降では、表示と、マシンが高密度の両方に接続されているであり、同時に標準密度が表示されます。 環境を操作するこれらのマシンを有効にするいくつかの機能が含まれています。  
  
-   Windows ことができます。 コンテンツを、"のテキストおよびその他の項目拡大または縮小する"を使用してデバイスを調整する (Windows XP 以降で使用可能) を設定します。  
  
-   Windows 8.1 以降を異なるピクセル密度の表示との間を移動すると、一致するようにほとんどのアプリケーション コンテンツを自動的にスケールします。 プライマリ ディスプレイ (200% スケーリング) 高密度で、セカンダリ ディスプレイ標準密度 (100%)、ときに Windows を自動的にスケール アプリケーション ウィンドウの内容セカンダリ ディスプレイで (1 ピクセルの表示で表示された各 4 ピクセル、アプリケーションの場合)。  
  
-   Windows は既定で右側のピクセルの密度のスケーリングと表示 (Windows 7 以降では、OEM が構成可能な) の距離を表示します。  
  
-   Windows は 280 ppi の時点で Windows 8.1 S14) を超える新しいデバイスのによっては 250% にコンテンツを自動的にスケールできます。  
  
 Windows には、増加したピクセル数を活用するために UI のスケール アップを処理する方法があります。 アプリケーション opts にこのシステムに"system 解像度に対応します"を宣言すること自体によって こうしないアプリケーションは、システムによって拡大/縮小されます。 ここでアプリケーション全体は、一様に分布のピクセル拡大「あいまい」のユーザー エクスペリエンスになります。 例えば:  
  
 ![DPI 問題あいまい](../extensibility/media/dpi-issues-fuzzy.png "DPI 問題あいまい")  
  
 Visual Studio DPI スケーリングに対応するの中にオプトインを指定し、したがってはされません「仮想化します」  
  
 Windows (および Visual Studio) は、スケール係数は、システムによって設定を処理する場合のさまざまな方法である必要が、いくつかの UI テクノロジを活用します。 例えば:  
  
-   WPF では、(ユニット数、ピクセル単位ではない) は、デバイスに依存しない方法でコントロールを測定します。 WPF の UI は、現在の DPI 用に自動的にスケーリングします。  
  
-   UI フレームワークに関係なくすべてのテキストのサイズはポイント単位で表され、のでシステムによって DPI に依存しないとして扱われます。 Win32、WinForms と WPF のテキストを既にスケール アップ正しくディスプレイ デバイスに描画した場合。  
  
-   Win32/WinForms ダイアログ、および windows があるグリッド、フロー、およびテーブル レイアウト パネル経由などのテキストのサイズを変更するレイアウトを有効にすることを意味します。 これらには、フォント サイズを増やすときにスケールされませんハードコーディング ピクセルの場所の回避が有効にします。  
  
-   システムによって提供されるアイコンまたはシステム メトリック (たとえば、SM_CXICON および SM_CXSMICON) に基づいて、リソースは既にスケール アップします。  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>古い Win32 (GDI、GDI +) および WinForms ベースの UI  
 WPF では高 DPI が認識既に Win32 GDI ベース コードの大部分書き込まれませんでした最初に留意 DPI 認識と。 Windows には、DPI スケール Api が用意されています。 Win32 の問題を修正プログラムは、製品間で常にこれらを使用してください。 Visual Studio には、ヘルパーが提供されている機能を複製して、製品全体にわたる一貫性を保つことを避けるためのクラス ライブラリです。  
  
## <a name="high-resolution-images"></a>高解像度のイメージ  
 このセクションでは、主に Visual Studio 2013 を拡張する開発者です。 Visual Studio 2015、Visual Studio に組み込まれているイメージのサービスを使用します。 多くのバージョンの Visual Studio のサポート/ターゲットする必要があるあり、したがって 2015年の イメージのサービスを使用してオプションではありません、以前のバージョンが存在しないためこともあります。 このセクションでもするからです。  
  
## <a name="scaling-up-images-that-are-too-small"></a>イメージが小さすぎることのスケール アップ  
 イメージが小さすぎることを「スケール アップ」と GDI といくつかの一般的な方法を使用して WPF 上にレンダリングされることができます。 DPI ヘルパーのマネージ クラスは、内部および外部の Visual Studio インテグレーター アドレス アイコン、ビットマップ、imagestrips、および imagelists のスケーリングに使用できます。 Win32 ベースのネイティブ C と c++ のヘルパーを HICON、HBITMAP、HIMAGELIST、および VsUI::GdiplusImage を拡張するために利用できます。 通常、ビットマップのスケールでは、ヘルパー ライブラリへの参照を含めた後に 1 行の変更のみが必要です。 例えば:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Imagelist のスケーリングは、imagelist が、読み込み時に完了またはが実行時に追加されるかどうかによって異なります。 読み込み時に完了すると場合、は、ビットマップのと同様に、imagelist に LogicalToDeviceUnits() を呼び出します。 コードは、イメージ リストを作成する前に個々 のビットマップを読み込む必要がある、ときに imagelist のイメージ サイズを調整することを確認してください。  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 ネイティブ コードは、次のように、イメージ リストを作成するときに、ディメンションを拡張できます。  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 ライブラリ内の関数は、サイズ変更のアルゴリズムを指定することを許可します。 ときに imagelists に配置するイメージをスケーリングは透過性、使用される背景色を指定することを確認または NearestNeighbor スケーリング (これにより 125% と 150% でゆがみ) を使用します。  
  
 参照してください、 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN のドキュメントです。  
  
 次の表は、スケール係数を対応する DPI でイメージをスケーリングする方法の例に示します。 緑の画像を表す (100 ~ 200% DPI scaling) Visual Studio 2013 の時点で、ベスト プラクティス。  
  
 ![DPI 問題 (スケーリング)](../extensibility/media/dpi-issues-scaling.png "DPI 問題 (スケーリング)")  
  
## <a name="layout-issues"></a>レイアウトの問題  
 絶対位置 (ピクセル単位) では具体的を使用してではなく、スケール、UI には相互に関連したは、ポイントを保持することで、主に、一般的なレイアウトに問題を回避できます。 例えば:  
  
-   レイアウトとテキストの位置は、スケール アップしたイメージのアカウントを調整する必要があります。  
  
-   グリッド内の列には、幅、スケール アップしたテキストに合わせて調整が必要です。  
  
-   サイズのハードコーディングまたは要素の間にスペースは、スケール アップする必要があります。 テキストの寸法にのみ基づくサイズは、フォントが自動的にスケール アップしたために通常問題ありません。  
  
 ヘルパー関数では使用、 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> X と Y 軸上の拡張を許可するクラス。  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (関数により、拡張する X と Y 軸)  
  
-   int 領域 = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   int 高さ VsUI::DpiHelper::LogicalToDeviceUnitsY(5); を =  
  
 四角形、ポイント、およびサイズなどのオブジェクトをスケーリングできる LogicalToDeviceUnits オーバー ロードがあります。  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>スケール イメージやレイアウトに DPIHelper ライブラリ/クラスを使用します。  
 Visual Studio DPI ヘルパー ライブラリは、ネイティブおよびマネージの形式で使用できる他のアプリケーションによって Visual Studio シェルの外部で使用できます。  
  
 ライブラリを使用するには、 [Visual Studio VSSDK 機能拡張のサンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples)および高 DPI_Images_Icons サンプルの複製  
  
 ソース ファイルで VsUIDpiHelper.h および VsUI::DpiHelper クラスの静的関数を呼び出します。  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  モジュール レベルまたはクラス レベルの静的変数では、ヘルパー関数を使用しないでください。 スレッドの同期も使用してスタティック ライブラリと順序初期化の問題が発生した可能性があります。 これらの静的変数を非静的メンバー変数に変換またはいずれかに (つまり、最初のアクセスが構築された取得) 関数をラップします。  
  
 Visual Studio 環境内で実行されるマネージ コードから DPI ヘルパー関数にアクセスします。  
  
-   使用するプロジェクトでは、シェル MPF の最新バージョンを参照する必要があります。 例えば:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   プロジェクトで参照していることを確認**System.Windows.Forms**、 **PresentationCore**、および**PresentationUI**です。  
  
-   コードを使用して、 **Microsoft.VisualStudio.PlatformUI** DpiHelper クラスの静的関数は名前空間を呼び出します。 (ポイント、サイズ、四角形、およびなど) のサポートされている型は、拡張機能を返す新しい関数には、オブジェクトが拡大/縮小指定にがあります。 例えば:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>ズーム可能な UI での WPF イメージの許容量を処理します。  
 WPF では、ビットマップがサイズ変更に自動的に WPF によって、現在の DPI ズーム レベルは画像や、大きなスクリーン ショットに適しては、見かけ上の許容量が導入されているために、メニュー項目のアイコンの適切な高品質双三次アルゴリズム (既定値) を使用して.  
  
 推奨事項:  
  
-   ロゴ イメージとバナー アートワーク、既定値の<xref:System.Windows.Media.BitmapScalingMode>サイズ変更モードを使用できます。  
  
-   メニュー項目とアイコン イメージの<xref:System.Windows.Media.BitmapScalingMode>が原因で他の歪みアーティファクト (200% から 300%) での許容を排除するときに使用する必要があります。  
  
-   大規模なズーム レベルを 100% (たとえば、250% または 350%) の倍数ではないの結果双三次アイコン イメージをスケーリングあいまい、色あせた UI になります。 結果が改善は、最初の 100% (200% または 300% など) の倍数の最大 NearestNeighbor でイメージをスケーリングとそこから双三次を使用したスケールして取得されます。 特殊なケースを参照してください。 詳細情報のレベルを WPF のイメージを大規模な DPI 用 prescaling です。  
  
 Microsoft.VisualStudio.PlatformUI 名前空間に DpiHelper クラス メンバーを提供する<xref:System.Windows.Media.BitmapScalingMode>バインディングを使用できます。 拡大縮小モード製品全体にわたる一様に分布、DPI スケール ファクターによってビットマップを制御する Visual Studio シェルが許可されます。  
  
 XAML での使用、次のように追加します。  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio シェルは、最上位のウィンドウとダイアログで既にこのプロパティを設定します。 Visual Studio で実行されている (WPF) ベースの UI には既に継承します。 設定は、特定の UI に反映しない場合、は、XAML/WPF UI のルート要素に設定することができます。 これが行われる場所は、Win32 の親を持つ要素でのポップアップを含めるし、デザイナー ウィンドウを実行しているプロセスに、Blend などです。  
  
 一部の UI は、Visual Studio テキスト エディターと (WPF) ベースのデザイナー (WPF デスクトップおよび Windows ストア) など、システム設定の DPI ズーム レベルとは無関係にスケーリングできます。 このような場合は、DpiHelper.BitmapScalingMode は指定しないでください。 エディターでこの問題を解決するには、カスタム プロパティを作成した IDE チーム タイトル RenderOptions.BitmapScalingMode になります。 システムと、UI の結合されたズーム レベルに応じて HighQuality または NearestNeighbor にそのプロパティ値を設定します。  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>特殊なケース: prescaling 大きい DPI レベルの WPF イメージ  
 非常に大きなズーム レベルを 100% (たとえば、および 250%、350%) の倍数ではない、あいまい、色あせた ui 双三次結果を含むアイコン イメージをスケーリングします。 これらのイメージ鮮明なテキストの横の印象錯覚のようにではほとんどです。 目に、テキストに関連してフォーカスが近い位置に、画像が表示されます。 この拡大されたサイズに拡大縮小の結果は、最初の 100% (200% または 300% など) の倍数の最大 NearestNeighbor でイメージをスケーリングと双三次残りの部分 (追加の 50%) を使用したスケールで改善できます。  
  
 次は、結果の違いの例の最初のイメージが拡大/縮小]-> [100% 向上倍スケール アルゴリズムで 200% 250% し双三次 100% だけで、もう 1 つに 250%]-> [です。  
  
 ![DPI 問題二重スケーリング例](../extensibility/media/dpi-issues-double-scaling-example.png "DPI スケーリング二重の例の問題")  
  
 各イメージ要素を表示するため、この倍スケール、XAML マークアップを使用する UI を有効にするには、変更する必要があります。 次の例では、DpiHelper ライブラリと Shell.12/14 を使用して Visual Studio での wpf 倍スケールを使用する方法を示します。  
  
 手順 1: は、300% 200% にイメージを Prescale し、NearestNeighbor を使用するようにします。  
  
 バインディング、または XAML マークアップ拡張機能で適用されるコンバーターを使用してイメージを prescale です。 例えば:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 イメージもテーマを指定する必要がある場合 (最も、すべてではない必要があります)、マークアップは、イメージと、事前のスケーリングのテーマを最初に異なるコンバーターを使用できます。 マークアップは、いずれかを使用して<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter>または<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>に必要な変換出力に依存します。  
  
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
  
 手順 2: は、最終的なサイズが現在の DPI の正しいことを確認します。  
  
 WPF は、uielement 設定 BitmapScalingMode プロパティを使用して現在の DPI の場合、UI を拡張、ためソースに 2 倍または 3 倍よりも大きくなります prescaled イメージを使用して、イメージ コントロール必要があります。 この特殊効果のカウンターの値にはいくつかの方法を次に示します。  
  
-   100% で元のイメージのディメンションがわかっている場合は、イメージ コントロールの正確なサイズを指定できます。 スケーリングする前に、UI のサイズが適用されるこれらのサイズが反映されます。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   元のイメージのサイズが不明の場合は、スケール ダウン最終的なイメージ オブジェクトを LayoutTransform を使用できます。 例えば:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>WebOC HDPI サポートを有効にします。  
 既定では、(たとえば、WPF または IWebBrowser2 インターフェイスで WebBrowser コントロール) WebOC コントロールは HDPI の検出とサポートを有効にしません。 内容の表示が高解像度のディスプレイには小さすぎると、埋め込みのコントロールになります。 次に、特定の web WebOC インスタンスでの高 DPI サポートを有効にする方法について説明します。  
  
 IDocHostUIHandler インターフェイスを実装する (上、MSDN の記事を参照してください、 [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx)インターフェイス)。  
  
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
  
 必要に応じて、ICustomDoc インターフェイスを実装 (上、MSDN の記事を参照してください、 [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx)インターフェイス)。  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 WebOC のドキュメントに IDocHostUIHandler を実装するクラスを関連付けます。 上記 ICustomDoc インターフェイスを実装した場合 WebOC のドキュメント プロパティは、使用するとすぐに、ICustomDoc にキャストし、IDocHostUIHandler を実装するクラスを渡して SetUIHandler メソッドを呼び出します。  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 ICustomDoc インターフェイスを実装しなかった場合、WebOC のドキュメント プロパティは、使用するとすぐにする必要があります、IOleObject にキャストし、IDocHostUIHandler を実装するクラスを渡して、SetClientSite メソッドを呼び出します。 GetHostInfo メソッドの呼び出しに渡される受け取る、DOCHOSTUIFLAG_DPI_AWARE フラグを設定します。  
  
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
  
1.  WebOC コントロールで、ドキュメントのプロパティが変更された場合は、IDocHostUIHandler クラスを使用したドキュメントを再関連付けする必要があります。  
  
2.  上記が機能しない場合、DPI フラグへの変更を取得していない WebOC の既知の問題があります。 この問題の修正の最も信頼性の高い方法では、光学 WebOC、ズームのパーセンテージの 2 つの異なる値で 2 つの呼び出しを意味のズームを切り替えるです。 さらに、この回避策が必要な場合、移動呼び出しごとに実行しなければならない場合があります。  
  
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