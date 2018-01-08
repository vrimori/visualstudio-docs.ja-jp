---
title: "イメージのサービスとカタログ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6f5d31e28c47dbcd4f17f7f1e1bc0ac6a8755d5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="image-service-and-catalog"></a>イメージ サービスとカタログ
このクックブックには、ガイダンスとベスト プラクティスを採用する Visual Studio イメージ サービスと Visual Studio 2015 で導入されたイメージ カタログが含まれています。  
  
 Visual Studio 2015 で導入されたイメージのサービスにより、開発者は、デバイスと表示されるコンテキストの正しいテーマを含む、イメージを表示するユーザーの選択したテーマの最適なイメージを取得します。 イメージのサービスを採用すると、資産管理、HDPI スケール、およびテーマに関連する主な問題点を排除するのに役立ちます。  
  
|||  
|-|-|  
|**現在の問題**|**ソリューション**|  
|背景色の描画|組み込みのアルファ ブレンド|  
|テーマ (一部) のイメージ|テーマのメタデータ|  
|ハイコントラスト モード|ハイ コントラストの代替のリソース|  
|異なる DPI モードの複数のリソースを必要があります。|ベクター ベースのフォールバックとともに選択可能なリソース|  
|イメージを複製します。|イメージの概念ごとの 1 つの識別子|  
  
 イメージのサービスを採用なぜですか。  
  
-   Visual Studio から常に最新の「ピクセルの完全な」イメージを取得します。  
  
-   送信して、独自のイメージを使用することができます。  
  
-   Windows が新しい DPI スケールを追加するときに、イメージをテストする必要はありません。  
  
-   実装に古いアーキテクチャ上の問題を対処します。  
  
 Visual Studio シェル ツールバー前に、と後イメージのサービスを使用します。  
  
 ![前に、と後イメージ サービス](../extensibility/media/image-service-before-and-after.png "前に、と後イメージのサービス")  
  
## <a name="how-it-works"></a>しくみ  
 イメージ サービスは、サポートされている UI フレームワークに適したビットマップ イメージを指定できます。  
  
-   WPF: BitmapSource  
  
-   WinForms: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 イメージ サービスのフロー ダイアグラム  
  
 ![サービスのフロー ダイアグラムをイメージ](../extensibility/media/image-service-flow-diagram.png "イメージのサービスのフロー ダイアグラム")  
  
 **イメージ モニカー**  
  
 イメージ モニカー (または略してモニカー) は、イメージ アセットまたはイメージ ライブラリでイメージ リストのアセットを一意に識別する GUID と ID のペアです。  
  
 **既知のモニカー**  
  
 イメージ モニカーが含まれている場合、Visual Studio イメージ カタログとパブリックに使用できる任意の Visual Studio のコンポーネントまたは拡張機能のセット。  
  
 **イメージ マニフェスト ファイル**  
  
 イメージ マニフェスト (.imagemanifest) ファイルは、これらの資産および実際のイメージまたは各アセットを表すイメージを表すモニカーのイメージ資産のセットを定義する XML ファイルです。 レガシの UI サポートのためのイメージ リストや画像マニフェストは、スタンドアロンのイメージを定義できます。 また、ときに、これらの資産の表示方法を変更する資産と各アセットの背後にある個々 のイメージのどちらかに設定できる属性があります。  
  
 **イメージ マニフェスト スキーマ**  
  
 イメージの完了マニフェストは、このようになります。  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Import, Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **シンボル**  
  
 読みやすさとメンテナンスに役立てるためとイメージ マニフェストは、属性値のシンボルを使用できます。 シンボルは、次のように定義されています。  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**サブ要素**|**定義**|  
|インポート|現在のマニフェストで使用する指定されたマニフェスト ファイルのシンボルのインポート|  
|GUID|シンボルの GUID を表し、GUID の書式設定と一致する必要があります。|  
|ID|シンボルの ID を表し、負でない整数でなければなりません|  
|String|シンボルは、任意の文字列値を表します|  
  
 シンボルは、大文字と小文字、および参照 $(symbol-name) 構文を使用するには。  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 すべてのマニフェストには、一部のシンボルが定義されています。 これらの Uri 属性で使用できる、\<ソース > または\<インポート > 要素をローカル コンピューター上の参照パス。  
  
|||  
|-|-|  
|**シンボル**|**説明**|  
|CommonProgramFiles|%Commonprogramfiles% 環境変数の値|  
|LocalAppData|LocalAppData 環境変数の値|  
|ManifestFolder|マニフェスト ファイルを含むフォルダー|  
|マイ ドキュメント|現在のユーザーの [マイ ドキュメント] フォルダーの完全なパス|  
|ProgramFiles|%Programfiles% 環境変数の値|  
|システム|Windows \system32 フォルダー|  
|%Windir%|WinDir 環境変数の値|  
  
 **イメージ**  
  
 \<イメージ > 要素は、モニカーで参照できるイメージを定義します。 GUID と ID をまとめると、イメージのモニカーを形成します。 イメージのモニカーは、全体のイメージ ライブラリ全体で一意である必要があります。 複数のイメージに特定のモニカーがある場合、ライブラリのビルド中に発生した 1 つ目は保持されているです。  
  
 これによりには、少なくとも 1 つのソースが含まれる必要があります。 サイズに依存しないソースは、サイズ、広い範囲にわたる最適な結果がもたらすされますが、必須ではありません。 定義されていないサイズのイメージのサービスが要求するかどうか、\<イメージ > 要素のサイズに依存しないソースがないと、サービスは、最適なサイズに固有のソースを選択し、要求されたサイズに拡大します。  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|GUID|[必須]イメージのモニカーの GUID 部分|  
|ID|[必須]イメージのモニカーの ID 部分|  
|AllowColorInversion|[省略可能で、既定値は true]イメージが、暗い背景で使用するとは逆にプログラムでの色を持つかどうかを示します。|  
  
 **ソース**  
  
 \<ソース > 要素が 1 つのイメージ ソース アセット (XAML および PNG) を定義します。  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|URI|[必須]定義する URI からイメージを読み込むことができます。 次のいずれかを指定できます。<br /><br /> A [Pack URI](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx)アプリケーションを使用して:///機関<br />-絶対コンポーネント リソース参照<br />-ネイティブ リソースを含むファイルへのパス|  
|背景|[オプション]ソースを使用するものではバック グラウンドの種類にどのようなことを示します。<br /><br /> 次のいずれかを指定できます。<br /><br /> *ライト:*ソースは、明るい背景で使用できます。<br /><br /> *濃い:*ソースは、暗い背景で使用できます。<br /><br /> *ハイコントラスト:*ソースは、ハイ コントラスト モードで、色の背景で使用できます。<br /><br /> *HighContrastLight:*ハイ コントラスト モードのライト バック グラウンドでは、ソースを使用できます。<br /><br /> *HighContrastDark:*ソースは、ハイ コントラスト モードで、暗い背景で使用できます。<br /><br /> バック グラウンド属性を省略すると、すべてのバック グラウンドで、ソースを使用できます。<br /><br /> バック グラウンドがある場合*ライト*、*濃い*、 *HighContrastLight*、または*HighContrastDark*ソースの色を反転ことはありません。 バック グラウンドを省略した場合またはに設定*ハイコントラスト*、ソースの色の反転は、イメージのによって制御されます**AllowColorInversion**属性。|  
|||  
  
 A\<ソース > 要素には、次の省略可能なサブ要素の 1 つだけ持つことができます。  
  
||||  
|-|-|-|  
|**要素**|**属性 (すべてが必須)**|**定義**|  
|\<サイズ >|[値]|ソースは、指定されたサイズ (デバイスのユニット数) のイメージの適用されます。 画像は四角形になります。|  
|\<SizeRange >|MinSize、MaxSize|ソースは、包括的 (デバイス単位で) の MaxSize を MinSize からイメージに使用されます。 画像は四角形になります。|  
|\<ディメンション >|幅、高さ|ソースは、指定した幅と高さ (デバイス単位) のイメージの適用されます。|  
|\<DimensionRange >|MinWidth、MinHeight、<br /><br /> MaxWidth、MaxHeight|ソースは、包括的イメージの幅/高さの最小値から最大の幅と高さ (デバイス単位で) に使用されます。|  
  
 A\<ソース > 要素は省略可能なこともできます\<NativeResource > サブ要素を定義する、\<ソース > マネージ アセンブリではなく、ネイティブ アセンブリから読み込まれる。  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|型|[必須]ネイティブ リソース、XAML または PNG のいずれかの種類|  
|ID|[必須]ネイティブ リソースの整数 ID の部分|  
  
 **ImageList**  
  
 \<ImageList > 要素が 1 つのストリップに返すことができるイメージのコレクションを定義します。 必要に応じて、ストリップがオンデマンドで作成されています。  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|GUID|[必須]イメージのモニカーの GUID 部分|  
|ID|[必須]イメージのモニカーの ID 部分|  
|外部|[省略可能で、既定値は false]イメージ モニカーが現在のマニフェストでイメージを参照するかどうかを示します。|  
  
 含まれているイメージのモニカーを現在のマニフェストで定義されているイメージを参照する必要はありません。 イメージ ライブラリに含まれているイメージが見つからない場合、空のプレース ホルダー イメージは、代わりに使用されます。  
  
## <a name="using-the-image-service"></a>イメージのサービスを使用します。  
  
### <a name="first-steps-managed"></a>最初の手順 (マネージ)  
 イメージのサービスを使用するには、次のアセンブリの一部または全部への参照をプロジェクトに追加する必要があります。  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   組み込みイメージ カタログ KnownMonikers を使用するかどうかは必須  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   使用するかどうかは必ず**CrispImage**と**ImageThemingUtilities**の WPF UI  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   使用するかどうかは必ず、 **ImageMoniker**と**ImageAttributes**型  
  
    -   **EmbedInteropTypes**設定する必要がある true に設定  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   使用するかどうかは必ず、 **IVsImageService2**型  
  
    -   **EmbedInteropTypes**設定する必要がある true に設定  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   使用するかどうかは必ず、 **BrushToColorConverter** 、ImageThemingUtilities 用**。ImageBackgroundColor**の WPF UI  
  
-   **Microsoft.VisualStudio.Shell です。\<VSVersion >.0**  
  
    -   使用するかどうかは必ず、 **、IVsUIObject**型  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   WinForms に関連する UI ヘルパーを使用するかどうかは必須  
  
    -   **EmbedInteropTypes**設定する必要がある true に設定  
  
### <a name="first-steps-native"></a>最初の手順 (ネイティブ)  
 イメージのサービスを使用するには、プロジェクトに次のヘッダーの一部またはすべてを含める必要があります。  
  
-   **KnownImageIds.h**  
  
    -   組み込みのイメージのカタログを使用するかどうかは必ず**KnownMonikers**は使用できませんが、 **ImageMoniker**から値を返す場合などの型**IVsHierarchy GetGuidProperty**または**GetProperty**呼び出しです。  
  
-   **KnownMonikers.h**  
  
    -   組み込みのイメージのカタログを使用するかどうかは必ず**KnownMonikers**です。  
  
-   **ImageParameters140.h**  
  
    -   使用するかどうかは必ず、 **ImageMoniker**と**ImageAttributes**型です。  
  
-   **VSShell140.h**  
  
    -   使用するかどうかは必ず、 **IVsImageService2**型です。  
  
-   **ImageThemingUtilities.h**  
  
    -   必要なイメージのサービスをテーマを処理することがないかどうか。  
  
    -   イメージ サービスは、イメージのテーマを処理できる場合は、このヘッダーを使用しないでください。  
  
-   **VSUIDPIHelper.h**  
  
    -   現在の DPI を取得する DPI ヘルパーを使用するかどうかに必要です。  
  
## <a name="how-do-i-write-new-wpf-ui"></a>新しい WPF UI を記述する方法は?  
  
1.  上記の必要なアセンブリ参照を追加することによって開始をプロジェクトに最初のセクションの手順です。 それらのすべての追加、参照だけが必要な追加する必要はありません。 (注: を使用している場合やへのアクセスを持って**色**の代わりに**ブラシ**への参照をスキップすることができますし、**ユーティリティ**コンバーターが不要なため、します)。  
  
2.  目的のイメージを選択し、そのモニカーを取得します。 使用して、 **KnownMoniker**、または独自のカスタム イメージとモニカーがある場合、独自に使用します。  
  
3.  追加**CrispImages** XAML にします。 (詳しくは、次の例を参照してください)。  
  
4.  設定、 **ImageThemingUtilities.ImageBackgroundColor** UI 階層内のプロパティです。 (これは、背景色がわかっている、必ずしもでない場所に設定する必要があります、 **CrispImage**)。(詳しくは、次の例を参照してください)。  
  
```xaml  
<Window  
  x:Class="WpfApplication.MainWindow"  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"  
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">  
  <Window.Resources>  
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>  
  </Window.Resources>  
  <StackPanel Background="White" VerticalAlignment="Center"   
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">  
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />  
  </StackPanel>  
</Window>  
```  
  
 **既存の WPF UI を更新する方法は?**  
  
 既存の WPF UI の更新は、次の 3 つの基本的な手順で構成される比較的単純なプロセスです。  
  
1.  すべて置換\<イメージ > で、UI 内の要素\<CrispImage > 要素  
  
2.  モニカーの属性をすべてのソース属性を変更します。  
  
    -   決して変化して、イメージを使用している場合**KnownMonikers**、そのプロパティを静的にバインド、 **KnownMoniker**です。 (上記の例を参照してください)。  
  
    -   決して変化して、イメージ、独自のカスタム イメージを使用している場合は、静的にバインド、独自のモニカー。  
  
    -   イメージを変更できる場合は、プロパティの変更を通知するコードのプロパティにモニカー属性をバインドします。  
  
3.  任意の場所、UI 階層で次のように設定します。 **ImageThemingUtilities.ImageBackgroundColor**させることを確認して色の反転が正常に動作します。  
  
    -   これを使用する必要があります、 **BrushToColorConverter**クラスです。 (上記の例を参照してください)。  
  
## <a name="how-do-i-update-win32-ui"></a>Win32 の UI を更新する方法は?  
 イメージの生の読み込みを置換する適切な場所には、コードに、次を追加します。 必要に応じて、HIMAGELIST と HICONs とようなを返すための値を切り替えます。  
  
 **イメージのサービスを取得します。**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **イメージを要求します。**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>WinForms UI を更新する方法は?  
 イメージの生の読み込みを置換する適切な場所には、コードに、次を追加します。 必要に応じて、アイコンとビットマップを返すための値を切り替えます。  
  
 **参考になったステートメントを使用します。**  
  
```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **イメージのサービスを取得します。**  
  
```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **イメージを要求します。**  
  
```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>新しいツール ウィンドウのイメージ モニカーを使用する方法  
 Visual Studio 2015 用の VSIX パッケージ プロジェクト テンプレートが更新されました。 新しいツール ウィンドウを作成するには、VSIX プロジェクトを右クリックし、[新しい項目の追加] を選択(Ctrl + Shift + A)。 [プロジェクトの言語の機能拡張ノードで、「カスタム ツール] ウィンドウで」を選択して、ツール ウィンドウの名前を指定し、「追加」ボタンを押します。  
  
 これらは、ツール ウィンドウのモニカーを使用する重要な場所です。 各手順に従います。  
  
1.  ツール ウィンドウ タブ タブ取得小さいときに十分な (Ctrl + Tab ウィンドウの切り替えにも使用されます)。  
  
     派生したクラスのコンス トラクターにこの行を追加、 **ToolWindowPane**型。  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  ツール ウィンドウを開くコマンド。  
  
     パッケージの .vsct ファイルでは、ツール ウィンドウのコマンド ボタンを編集します。  
  
    ```xml  
    <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <!-- Replace this KnownMoniker with your desired ImageMoniker -->  
      <Icon guid="ImageCatalogGuid" id="Blank" />  
      <!-- Add this -->  
      <CommandFlag>IconIsMoniker</CommandFlag>  
      <Strings>  
        <ButtonText>MyToolWindow</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
 **既存のツール ウィンドウのイメージ モニカーを使用する方法**  
  
 イメージのモニカーを使用する既存のツール ウィンドウを更新することは、新しいツール ウィンドウを作成するための手順に似ています。  
  
 これらは、ツール ウィンドウのモニカーを使用する重要な場所です。 各手順に従います。  
  
1.  ツール ウィンドウ タブ タブ取得小さいときに十分な (Ctrl + Tab ウィンドウの切り替えにも使用されます)。  
  
    1.  派生したクラスのコンス トラクターでこれらの行を削除 (存在する場合)、 **ToolWindowPane**型。  
  
        ```csharp  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  手順 1 の参照、「操作方法、新しいツール ウィンドウのイメージ モニカーを使用しますか?」 前のセクションです。  
  
2.  ツール ウィンドウを開くコマンド。  
  
    -   手順 2 を参照して、「操作方法、新しいツール ウィンドウのイメージ モニカーを使用しますか?」 前のセクションです。  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>.Vsct ファイル内のイメージ モニカーを使用する方法  
 以下のコメントが付けられた行が示すとおり、.vsct ファイルを更新します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we're using the Guid for the VS image catalog.  
             Change the id attribute to be the ID of the desired image moniker. -->  
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <CommandFlag>DefaultInvisible</CommandFlag>  
        <CommandFlag>DefaultDisabled</CommandFlag>  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>IconAndText</CommandFlag>  
        <!-- Add the IconIsMoniker CommandFlag -->  
        <CommandFlag>IconIsMoniker</CommandFlag>  
        <Strings>  
          <ButtonText>Quick Fixes...</ButtonText>  
          <CommandName>Show Quick Fixes</CommandName>  
          <CanonicalName>ShowQuickFixes</CanonicalName>  
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>  
        </Strings>  
      </Button>  
    </Buttons>  
  </Commands>  
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->  
  <Symbols>  
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />  
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">  
      <IDSymbol name="cmdidMyCommand" value="0x9437" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```  
  
 **What-if .vsct ファイルは、Visual Studio の以前のバージョンによって読み取られるも必要ですか。**  
  
 Visual Studio の旧バージョンを認識しない、 **IconIsMoniker**コマンド フラグ。 イメージのサービスからのイメージは、サポートは引き続き古いバージョンの Visual Studio で旧式のイメージを使用するバージョンの Visual Studio で使用できます。 これを行うには、は変更されない (および Visual Studio の旧バージョンと互換性のあるため)、.vsct ファイルのままにし、CSV (コンマ区切り値) をマップするファイルを作成する .vsct ファイルで定義されている GUID と ID のペアから\<ビットマップ > イメージに要素モニカーの GUID と ID のペア。  
  
 マッピングの CSV ファイルの形式です。  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 CSV ファイルは、パッケージと共にデプロイされ、その場所が指定の**IconMappingFilename**のプロパティ、 **ProvideMenuResource**パッケージ属性。  
  
```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 **IconMappingFilename**がいずれかの相対パスに暗黙的にルート $PackageFolder$ (例のように、上記)、または絶対パスが明示的に @"%UserProfile%\ などの環境変数で定義されているディレクトリをルートとdir1\dir2\MyMappingFile.csv"です。  
  
## <a name="how-do-i-port-a-project-system"></a>プロジェクト システムを移植する方法は?  
 **プロジェクトの ImageMonikers を提供する方法**  
  
1.  実装**VSHPROPID_SupportsIconMonikers** 、プロジェクトの**IVsHierarchy**、true を返します。  
  
2.  どちらかを実装**VSHPROPID_IconMonikerImageList** (元のプロジェクトが使用されている場合**VSHPROPID_IconImgList**) または**VSHPROPID_IconMonikerGuid**、 **VSHPROPID_IconMonikerId**、 **VSHPROPID_OpenFolderIconMonikerGuid**、 **VSHPROPID_OpenFolderIconMonikerId** (元のプロジェクトが使用されている場合**VSHPROPID_IconHandle**と**VSHPROPID_OpenFolderIconHandle**)。  
  
3.  拡張ポイントを要求する場合に、アイコンの「レガシ」のバージョンを作成するアイコンの元の VSHPROPIDs の実装を変更します。 **IVsImageService2**をこれらのアイコンを取得するために必要な機能を提供します  
  
 **VB の場合の特別な要件味を c# プロジェクト/**  
  
 実装するだけ**VSHPROPID_SupportsIconMonikers** 、プロジェクトがあることを検出した場合、**最も外側のフレーバー**です。 それ以外の場合、実際の最も外側のフレーバーが実際には、イメージのモニカーをサポートしない可能性し、基本のフレーバーが効果的に"hide"カスタマイズされたイメージ。  
  
 **CPS 内のイメージ モニカーが使用する方法**  
  
 手動でまたはプロジェクト システムの機能拡張 SDK に付属している項目テンプレートを使用して、CPS (共通プロジェクト システム) でカスタム イメージの設定を行うことができます。  
  
 **プロジェクト システムの拡張機能 SDK を使用します。**  
  
 ある手順に従って[プロジェクトの種類/項目の種類のカスタム アイコンを提供](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md)CPS イメージをカスタマイズします。 CPS の詳細についてはあります[Visual Studio プロジェクト システムの機能拡張のドキュメント](https://github.com/Microsoft/VSProjectSystem)  
  
 **ImageMonikers を使用して手動で**  
  
1.  実装およびエクスポート、 **IProjectTreeModifier**プロジェクト システム内のインターフェイスです。  
  
2.  決定**KnownMoniker**またはカスタム イメージのモニカーを使用します。  
  
3.  **ApplyModifications**メソッドを次の操作を新しいツリーを返す前に、メソッドのどこかに、次の例。  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  NewTree メソッドと同様に、目的のモニカーに渡すことで、カスタム イメージを設定するには、新しいツリーを作成する場合、次の例。  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
    ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  
  
    return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                 /*filePath*/<value>,  
                                                 /*browseObjectProperties*/<value>,  
                                                 icon,  
                                                 expandedIcon);  
    ```  
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>モニカ ベース イメージ ストリップに実際のイメージ ストリップから変換する方法  
 **HIMAGELISTs をサポートする必要があります。**  
  
 既存のイメージ ストリップがあるがイメージ サービスを使用して更新するイメージ リストを受け渡すを必要とする Api によって制約は、コードの場合は、イメージのサービスの利点を享受できます。 モニカ ベース イメージ ストリップを作成するには、既存のモニカーからマニフェストを作成するのには、以下の手順に従います。  
  
1.  実行、 **ManifestFromResources**ツール、イメージ ストリップを渡します。 これにより、ストリップのマニフェストが生成されます。  
  
    -   お勧めします。 その使用状況に合わせてマニフェストの既定以外の名前を提供します。  
  
2.  のみを使用する場合**KnownMonikers**、次の操作します。  
  
    -   置換、\<イメージ > セクションを使用したマニフェストの\<イメージ/>。  
  
    -   すべてのサブイメージ Id を削除 (で何も\<imagestrip 名 > _ #)。  
  
    -   AssetsGuid 記号とその使用状況に合わせてイメージ ストリップ シンボルお勧めします。 名前を変更します。  
  
    -   各を置き換える**ContainedImage**の各 $(ImageCatalogGuid) の GUID を置き換える**ContainedImage**の ID では、$(\<モニカー >)、各に外部="true"属性を追加および**ContainedImage**  
  
        -   \<モニカー > で置き換える必要があります、 **KnownMoniker**イメージと一致するが、"KnownMonikers"。 名前から削除されます。  
  
    -   追加 < インポート Manifest="$(ManifestFolder)\\< 相対パスをインストールするディレクトリ パス\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest"/\>の先頭に、\<シンボル > セクションです。  
  
        -   相対パスは、マニフェストの作成の設定で定義されている配置場所によって決まります。  
  
3.  実行、 **ManifestToCode**既存のコードがあるイメージ ストリップに対してイメージ サービスのクエリを使用して、モニカーを持つように、ラッパーを生成するツールです。  
  
    -   推奨: ラッパーとその使用状況に合わせて名前空間に既定以外の名前を提供します。  
  
4.  すべては、追加すると、セットアップの作成と展開、およびイメージのサービスと、新しいファイルを操作するには、その他のコード変更します。  
  
 サンプルのマニフェストにどのように表示する、内部および外部の画像を含める:  
  
```xml  
<?xml version="1.0"?>  
<ImageManifest  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  
  <Symbols>  
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest  
         where $(ManifestFolder) is the deployed location of this manifest. -->  
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />  
  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />  
    <ID Name="MyImage_0" Value="100" />  
    <ID Name="MyImage_1" Value="101" />  
    <ID Name="InternalList" Value="1001" />  
    <ID Name="ExternalList" Value="1002" />  
  </Symbols>  
  
  <Images>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">  
      <Source Uri="$(Resources)/MyImage_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">  
      <Source Uri="$(Resources)/MyImage_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  
  <ImageLists>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />  
    </ImageList>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />  
    </ImageList>  
  </ImageLists>  
  
</ImageManifest>  
```  
  
 **HIMAGELISTs をサポートする必要はありません。**  
  
1.  指定の**KnownMonikers**イメージ ストリップ内にある画像を一致や、イメージ ストリップの画像の独自のモニカーを作成します。  
  
2.  代わりに、モニカーを使用するイメージ ストリップに必要なインデックスにある画像の取得に使用されるどのようなマッピングを更新します。  
  
3.  更新されたマッピングを介してモニカーを要求するイメージのサービスを使用するようコードを更新します。 (更新する可能性があります**CrispImages**のマネージ コード、またはイメージのサービスからのようなまたは HICONs を要求しているとネイティブ コードの別の場所に渡すことです)。  
  
## <a name="testing-your-images"></a>イメージのテスト  
 イメージ ライブラリ ビューアー ツールを使用して、すべてが正しく作成されているかどうかを確認する、画像マニフェストをテストすることができます。 このツールを見つけることができます、 [Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx)です。 このツールおよびその他のドキュメントが記載されて[ここ](http://aka.ms/VSImageThemeTools)です。  
  
## <a name="additional-resources"></a>その他の技術情報  
  
### <a name="samples"></a>サンプル  
 GitHub の Visual Studio のサンプルのいくつかは、さまざまな Visual Studio 機能拡張ポイントの一部として、イメージのサービスを使用する方法を示す更新されています。  
  
 確認[http://github.com/Microsoft/VSSDK-Extensibility-Samples](http://github.com/Microsoft/VSSDK-Extensibility-Samples)最新のサンプルです。  
  
### <a name="tooling"></a>ツール  
 イメージ サービスのサポート ツールのセットは、イメージのサービスで動作する UI の作成/更新支援するために作成されました。 各ツールの詳細については、ツールに付属するマニュアルを確認してください。 ツールはの一部として含める、 [Visual Studio 2015 SDK。](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 リソースのツールからマニフェストは、イメージ リソース (PNG や XAML) の一覧を取得し、イメージのサービスとそれらのイメージを使用するためのイメージのマニフェスト ファイルを生成します。  
  
 **ManifestToCode**  
  
 コード ツールにマニフェストは、イメージ マニフェスト ファイルを受け取りし、コード (C++、C# の場合、または VB) または .vsct ファイルでマニフェストの値を参照ラッパー ファイルを生成します。  
  
 **ImageLibraryViewer**  
  
 イメージ ライブラリ ビューアー ツールは、画像マニフェストを読み込むことができ、それらを Visual Studio のマニフェストが正しく作成されているかどうかを確認すると同じ方法で操作することができます。 ユーザーには、バック グラウンド、サイズ、DPI 設定、ハイ コントラスト、およびその他の設定を変更できます。 また、マニフェストのエラーを検出する読み込み情報が表示され、マニフェスト内の各イメージのソース情報が表示されます。  
  
## <a name="faq"></a>FAQ  
  
-   読み込むときに含める必要のある依存関係がある\<参照 Include="Microsoft.VisualStudio.* です。Interop.14.0.DesignTime"/> ですか?  
  
    -   EmbedInteropTypes の設定の相互運用機能のすべての Dll には、"true"を = です。  
  
-   My の拡張機能とイメージ マニフェストが展開する方法  
  
    -   .Imagemanifest ファイルをプロジェクトに追加します。  
  
    -   「VSIX に含める」が True に設定します。  
  
-   CPS プロジェクト システムを更新しているところです。 変更点を**ImageName**と**StockIconService**しますか?  
  
    -   o モニカーを使用する CPS が更新されたときにこれらは削除されました。 呼び出すが不要になった、 **StockIconService**、目的を渡すだけ**KnownMoniker**メソッドまたはプロパティを使用して、 **ToProjectSystemType()**でも拡張メソッドCPS のユーティリティです。 マッピングを見つけることができます**ImageName**に**KnownMonikers**下。  
  
        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  
  
    -   入力候補一覧プロバイダーを更新しているところです。 どのような**KnownMonikers**と古いに一致する**StandardGlyphGroup**と**StandardGlyph**値しますか?  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
        |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
        |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
        |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
        |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
        |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
        |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
        |GlyphGroupType|GlyphItemPublic|TypePublic|  
        |GlyphGroupType|GlyphItemInternal|TypeInternal|  
        |GlyphGroupType|GlyphItemFriend|TypeInternal|  
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||クラスファイル|  
        |GlyphAssembly||参照|  
        |GlyphLibrary||ライブラリ|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||ダイアログ|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||GoToNext|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||スニペット|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||再帰|  
        |GlyphXmlItem||タグ|  
        |GlyphJSharpProject||DocumentCollection|  
        |GlyphJSharpDocument||ドキュメント|  
        |GlyphForwardType||GoToNext|  
        |GlyphCallersGraph||の|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||疑問符|  
        |GlyphMaybeCaller||の|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||xmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|