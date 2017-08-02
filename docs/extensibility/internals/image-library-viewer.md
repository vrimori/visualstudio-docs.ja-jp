---
title: "イメージ ライブラリ ビューアー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# イメージ ライブラリ ビューアー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio イメージ ライブラリ ビューアー ツールは、読み込むし、イメージ マニフェスト、ユーザーは、Visual Studio のと同じ方法で操作できるようにするを検索できます。 ユーザーには、バック グラウンド、サイズ、DPI、ハイ コントラスト、およびその他の設定を変更できます。 ツールは、各イメージのマニフェストの読み込み情報が表示され、イメージ マニフェスト内の各イメージのソース情報を表示します。 このツールは、に便利です。  
  
1.  エラーの診断  
  
2.  カスタム イメージのマニフェストで確保属性が正しく設定します。  
  
3.  Visual Studio 拡張機能は、Visual Studio のスタイルに合わせてイメージを使用できるように、Visual Studio イメージ カタログでのイメージの検索  
  
 ![イメージ ライブラリ ビューアーのヒーロー](../../extensibility/internals/media/image-library-viewer-hero.png "Image Library Viewer Hero")  
  
 **イメージのモニカー**  
  
 イメージ モニカー (または略してモニカー) は、イメージ アセットまたはイメージ ライブラリにイメージの一覧の資産を一意に識別する GUID:ID ペアです。  
  
 **イメージのマニフェスト ファイル**  
  
 マニフェスト (.imagemanifest) のイメージ ファイルは、それらの資産と実際のイメージまたは各資産を表す画像を表すモニカーのイメージ資産のセットを定義する XML ファイルです。 レガシの UI サポートのためのイメージ リストやイメージのマニフェストは、スタンドアロンのイメージを定義できます。 また、特定の時点とそれらの資産の表示方法を変更する、資産または各アセットの背後にある個別のイメージのいずれかに設定できる属性が使用されます。  
  
 **マニフェスト スキーマの画像**  
  
 イメージの完了マニフェストは、次のようになります。  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Guid, ID, or String elements -->  
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
  
 読みやすさと保守に役立てるため、イメージのマニフェストは、属性値のシンボルを使用できます。 シンボルは、次のように定義されます。  
  
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
|インポート|最新のマニフェストで使用するための指定されたマニフェスト ファイルのシンボルをインポートします。|  
|Guid|シンボルは、GUID を表し、GUID の書式設定と一致する必要があります。|  
|ID|シンボルは、ID を表し、負でない整数でなければなりません。|  
|String|シンボルは、任意の文字列値を表します。|  
  
 シンボルは、大文字と小文字、および $(symbol-name) 構文を使用して参照には。  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 すべてのマニフェストに対しては、いくつかの記号があらかじめ定義されています。 これらの Uri の属性で使用できる、\< ソース> または \< インポート> をローカル コンピューターの参照パスの要素。  
  
|||  
|-|-|  
|**シンボル**|**説明**|  
|CommonProgramFiles|%Commonprogramfiles% 環境変数の値|  
|LocalAppData|LocalAppData 環境変数の値|  
|ManifestFolder|マニフェスト ファイルを含むフォルダー|  
|マイ ドキュメント|現在のユーザーのマイ ドキュメント フォルダーの完全なパス|  
|ProgramFiles|%Programfiles% 環境変数の値|  
|System|Windows \system32 フォルダー|  
|WinDir|WinDir 環境変数の値|  
  
 **イメージ**  
  
 \< イメージ> 要素は、モニカーで参照できるイメージを定義します。 GUID と ID をまとめると、イメージのモニカーを形成します。 イメージのモニカーは、全体のイメージ ライブラリ全体で一意である必要があります。 複数のイメージに指定したモニカーがある場合は、ライブラリのビルド中に発生した 1 つ目は保持されます。  
  
 少なくとも 1 つのソースを含んでいます。 サイズに依存しないソースは、幅広いサイズで最良の結果を与えるが、必須ではありません。 定義されていないサイズのイメージをサービスが要求されるかどうかは、\< イメージ> 要素のサイズに依存しないソースが存在しないと、サービスが最適なサイズに固有のソースを選択し、要求されたサイズに拡大します。  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|Guid|[必須]イメージのモニカーの GUID 部分|  
|ID|[必須]イメージのモニカーの ID 部分|  
|AllowColorInversion|[省略可能、既定値は true]イメージでの色をプログラムで、暗い背景で使用される場合が反転できるかどうかを示します。|  
  
 **ソース**  
  
 \< ソース> 要素は 1 つのイメージのソース資産 (XAML および PNG) を定義します。  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|URI|[必須]イメージを読み込むことを定義する URI。 次のいずれかを指定できます。<br /><br /> A [Pack URI](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) アプリケーションを使用して:///機関<br /><br /> 絶対コンポーネント リソース参照<br /><br /> -ネイティブ リソースを含むファイルへのパス|  
|背景|[省略可能]ソースが使用するための背景の種類にどのようなことを示します。<br /><br /> 次のいずれかを指定できます。<br /><br /> - *ライト*: 明るい背景には、ソースを使用できます。<br /><br /> - *濃い*: ソースは、暗い背景で使用できます。<br /><br /> - *ハイコントラスト*: ソースは、ハイ コントラスト モードで、色の背景で使用できます。<br /><br /> - *HighContrastLight*: ソースは、ハイ コントラスト モードのライト バック グラウンドで使用できます。<br /><br /> -*HighContrastDark*: ソースは、ハイ コントラスト モードで、暗い背景で使用できます。<br /><br /> 場合、 **バック グラウンド** 属性が省略された場合、ソースは、色の背景で使用できます。<br /><br /> 場合 **バック グラウンド** は *Light*, 、*ダーク*, 、*HighContrastLight*, 、または *HighContrastDark*, 、元の色を反転ことはありません。 場合 **バック グラウンド** を省略するかに設定 *ハイコントラスト*, 、元の色の反転は、イメージによって制御されます **AllowColorInversion** 属性です。|  
  
 A \< ソース> 要素は省略可能な次のサブ要素の 1 つだけであることができます。  
  
||||  
|-|-|-|  
|**要素**|**(すべての必要な) 属性**|**定義**|  
|\< サイズ>|値|デバイス単位で指定されたサイズのイメージのソースが使用されます。 画像は正方形になります。|  
|\< SizeRange>|MinSize、MaxSize|ソースは、範囲 (デバイス単位) の MaxSize を MinSize から画像に使用されます。 画像は正方形になります。|  
|\< ディメンション>|幅、高さ|ソースは、指定した幅と高さ (デバイス単位) のイメージの適用されます。|  
|\< DimensionRange>|MinWidth、MinHeight、<br /><br /> MaxWidth、MaxHeight|ソースは、範囲の幅/高さの最小値から最大の幅と高さ (デバイス単位) にイメージに使用されます。|  
  
 A \< ソース> 要素は省略可能なこともできます \< NativeResource> を定義するサブ要素、\< ソース> マネージ アセンブリではなく、ネイティブ アセンブリから読み込まれます。  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|型|[必須]XAML または PNG のいずれかのネイティブ リソースの種類|  
|ID|[必須]ネイティブ リソースの整数 ID 部分|  
  
 **イメージ リスト**  
  
 \< ImageList> 要素が 1 つのストリップに返すことができるイメージのコレクションを定義します。 必要に応じて、オンデマンドでストリップが構築されます。  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|Guid|[必須]イメージのモニカーの GUID 部分|  
|ID|[必須]イメージのモニカーの ID 部分|  
|[外部]|[省略可能、既定値は false]イメージのモニカーが、最新のマニフェストでイメージを参照するかどうかを示します。|  
  
 含まれているイメージのモニカーは、最新のマニフェストで定義されているイメージを参照する必要はありません。 イメージ ライブラリに含まれているイメージが見つからない場合、空のプレース ホルダー イメージは、代わりに使用されます。  
  
## <a name="how-to-use-the-tool"></a>ツールを使用する方法  
 **カスタム イメージのマニフェストを検証します。**  
  
 カスタム マニフェストを作成するには、マニフェストを生成する際、ManifestFromResources ツールを使用することをお勧めします。 カスタム マニフェストを検証するには、イメージ ライブラリ ビューアーを起動し、ファイルを選択 > パスを設定しています. ディレクトリの検索] ダイアログを開きます。 イメージのマニフェストを読み込むファイルの検索ディレクトリが使用されますが、またそれを使用、マニフェストでイメージを含む .dll ファイルを見つけるようになるようにこのダイアログ ボックスで、マニフェストと DLL のディレクトリの両方を含めるようにしてください。  
  
 ![イメージ ライブラリ ビューアーの検索](../../extensibility/internals/media/image-library-viewer-search.png "Image Library Viewer Search")  
  
 クリックして **を追加しています.** マニフェストとが対応する Dll を検索する新しい検索ディレクトリを選択します。 ツールには、これらの検索ディレクトリは注意してくださいし、変換オンとオフをオンまたはオフにするディレクトリ。  
  
 既定では、ツールは Visual Studio インストール ディレクトリを検索し、それらのディレクトリを検索ディレクトリの一覧に追加を試みます。 ツールを検索しないディレクトリを手動で追加することができます。  
  
 切り替えるツールを使用できるすべてのマニフェストが読み込まれると、 **バック グラウンド** 色、 **DPI**, 、**ハイ コントラスト**, 、または **ディザリングを行います** イメージのユーザーできることを確認するイメージの資産を検査して視覚的にことされて適切に描画されますのさまざまな設定です。  
  
 ![イメージ ライブラリ ビューアーの背景](../../extensibility/internals/media/image-library-viewer-background.png "Image Library Viewer Background")  
  
 背景色は、ライト、暗い、またはカスタムの値に設定できます。 "カスタム Color"を選択すると、色の選択] ダイアログ ボックスを開くし、容易な再現率後でのバック グラウンドのコンボ ボックスの下部にそのカスタムの色を追加します。  
  
 ![イメージ ライブラリ ビューアーのカスタム色](../../extensibility/internals/media/image-library-viewer-custom-color.png "Image Library Viewer Custom Color")  
  
 イメージ モニカーを選択すると、右側の [イメージの詳細] ウィンドウでそのモニカーの背後にある実際のイメージごとに情報が表示されます。 ウィンドウでは、名前または生 GUID:ID 値では、モニカーをコピーすることもできます。  
  
 ![イメージ ライブラリ ビューアーのイメージの詳細](../../extensibility/internals/media/image-library-viewer-image-details.png "Image Library Viewer Image Details")  
  
 各イメージ ソースの表示される情報テーマが適用されたことができるかどうかの背景を表示の種類が含まれていますまたはハイコントラストは有効なサイズをサポートしているまたはかどうかのサイズに依存しない、おりネイティブ アセンブリから提供されたイメージのかどうか。  
  
 ![イメージ ライブラリ ビューアーにテーマを設定可能](~/extensibility/internals/media/image-library-viewer-can-theme.png "Image Library Viewer Can Theme")  
  
 イメージ マニフェストを検証する場合は、マニフェスト、およびイメージの実際の場所に DLL を配置することをお勧めします。 相対パスが正しく動作していることができます、イメージ ライブラリを検索して、マニフェストとイメージ DLL を読み込むことと、これが確認されます。  
  
 **イメージのカタログ KnownMonikers の検索**  
  
 Visual Studio のスタイル設定に合わせて、Visual Studio 拡張機能は、Visual Studio イメージのカタログではなく作成と使用を独自のイメージを使用できます。 これにより、それらのイメージを維持する必要があるの利点は、Visual Studio をサポートするすべての DPI 設定で正しいなりますので、イメージが高解像度のバックアップ イメージを持つことが保証します。  
  
 イメージ ライブラリ ビューアーでは、ユーザーは、モニカーを表すイメージ アセットを検索してコードでそのモニカーを使用できるように検索するためにマニフェストを使用します。 イメージを検索するに検索ボックスに必要な検索語句を入力し、Enter キーを押します。 一致の件数は見つかった合計イメージから、マニフェストのすべてのページで、下部にあるステータス バーが表示されます。  
  
 ![イメージ ライブラリ ビューアーのフィルター](../../extensibility/internals/media/image-library-viewer-filter.png "Image Library Viewer Filter")  
  
 既存のマニフェストでイメージのモニカーを検索する場合を検索して、Visual Studio イメージ カタログのモニカーのみ、他の意図的にパブリックにアクセスできるモニカー、または独自のカスタム モニカーを使用することをお勧めします。 非パブリックなモニカーを使用する場合カスタム UI が壊れることがありますか、イメージ変更された予期しない場合、またはこれらの非パブリックなモニカーとイメージを変更または更新するとき。  
  
 また、GUID によって検索が可能です。 この種の検索は 1 つのマニフェストにリストをフィルター処理に役立つか、マニフェストの場合は、そのマニフェストの 1 つのサブセクションには、複数の Guid が含まれています。  
  
 ![イメージ ライブラリ ビューアーのフィルター GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Image Library Viewer Filter GUID")  
  
 最後に、ID を使用して検索も可能になります。  
  
 ![イメージ ライブラリ ビューアーのフィルター ID](../../extensibility/internals/media/image-library-viewer-filter-id.png "Image Library Viewer Filter ID")  
  
## <a name="notes"></a>ノート  
  
-   既定では、ツールは Visual Studio インストール ディレクトリにあるいくつかのイメージのマニフェストを取得します。 パブリックに利用可能なモニカーを持つ 1 つだけ、 **Microsoft.VisualStudio.ImageCatalog** マニフェストします。 GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (しないで **いない** カスタム マニフェストでは、この GUID をオーバーライド) の種類: KnownMonikers  
  
-   ツールは、アプリケーションが、実際に表示するのに数秒かかりますのでが見つかると、すべてのイメージのマニフェストを読み込むの起動時にしようとします。 またあります動作が遅いか応答していない、マニフェストを読み込み中にします。  
  
## <a name="sample-output"></a>出力例  
 このツールは、出力を生成しません。