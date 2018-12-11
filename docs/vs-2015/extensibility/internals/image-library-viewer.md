---
title: イメージ ライブラリ ビューアー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c0e277a123fe24da9824fae94b13eee686f5663
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778021"
---
# <a name="image-library-viewer"></a>イメージ ライブラリ ビューア
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio Image Library ビューアー ツールは、読み込みおよびユーザーが Visual Studio と同じ方法で操作できるように、イメージのマニフェストを検索できます。 ユーザーは、バック グラウンド、サイズ、DPI、ハイ コントラスト、およびその他の設定を変更できます。 このツールは、各イメージ マニフェストの読み込み情報を表示し、イメージ マニフェスト内の各イメージのソース情報を表示します。 このツールは、場合に便利です。  
  
1. エラーを診断します。  
  
2. カスタム イメージのマニフェストで確保属性が正しく設定します。  
  
3. Visual Studio 拡張機能は、Visual Studio のスタイルに合わせてイメージを使用できるように、Visual Studio イメージ カタログ内のイメージの検索  
  
   ![イメージ ライブラリ ビューアーのヒーロー](../../extensibility/internals/media/image-library-viewer-hero.png "イメージ ライブラリ ビューアーのヒーロー")  
  
   **イメージのモニカー**  
  
   イメージのモニカー (または略してモニカー) はのイメージ アセットまたはイメージ ライブラリにあるイメージの一覧の資産を一意に識別する GUID:ID のペアです。  
  
   **イメージ マニフェスト ファイル**  
  
   イメージ マニフェスト (.imagemanifest) ファイルは、これらの資産と実際のイメージまたは各資産を表すイメージを表すモニカーのイメージ アセットのセットを定義する XML ファイルです。 従来の UI サポートのイメージを一覧表示またはイメージ マニフェストは、スタンドアロン画像を定義できます。 さらに、ときに、これらの資産を表示する方法を変更する、資産または各資産の背後にある個別のイメージのいずれかに設定できる属性があります。  
  
   **イメージ マニフェスト スキーマ**  
  
   イメージの完了のマニフェストのようになります。  
  
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
  
 読みやすさと保守に役立てるため、イメージ マニフェストは、属性値のシンボルを使用できます。 このようなシンボルが定義されます。  
  
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
|インポート|現在のマニフェストで使用するための指定されたマニフェスト ファイルのシンボルをインポートします。|  
|GUID|シンボルは、GUID を表し、GUID の書式設定と一致する必要があります。|  
|ID|シンボルは、ID を表し、負でない整数でなければなりません。|  
|String|シンボルは、任意の文字列値を表します。|  
  
 シンボルは、大文字と小文字、および $(symbol-name) 構文を使用して参照には。  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 いくつかの記号は、すべてのマニフェストを事前定義されています。 これらの Uri の属性で使用できる、\<ソース > または\<インポート > 要素をローカル コンピューター上の参照のパス。  
  
|||  
|-|-|  
|**シンボル**|**説明**|  
|CommonProgramFiles|%Commonprogramfiles% 環境変数の値|  
|LocalAppData|LocalAppData 環境変数の値|  
|ManifestFolder|マニフェスト ファイルを含むフォルダー|  
|[マイ ドキュメント]|現在のユーザーのマイ ドキュメント フォルダーの完全なパス|  
|ProgramFiles|%Programfiles% 環境変数の値|  
|システム|Windows \system32 フォルダー|  
|%Windir%|WinDir 環境変数の値|  
  
 **イメージ**  
  
 \<イメージ > 要素は、モニカーで参照できるイメージを定義します。 GUID と組み合わされる ID は、イメージ モニカーを形成します。 イメージのモニカーは、全体のイメージ ライブラリ全体で一意である必要があります。 1 つ以上のイメージに指定したモニカーがある場合は、ライブラリのビルド中に発生した 1 つ目が保持される 1 つにします。  
  
 ソースの少なくとも 1 つ含める必要があります。 サイズに依存しないソースは、幅広いサイズで最適な結果を与えるが、必要はありません。 定義されていないサイズのイメージのサービスが求められるかどうか、\<イメージ > 要素のサイズに依存しないソースがないと、サービスが最適なサイズに固有のソースを選択し、要求されたサイズに拡大します。  
  
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
|AllowColorInversion|[省略可能、既定値は true]イメージが黒っぽい背景で使用されるときに反転されるプログラムでの色を持つかどうかを示します。|  
  
 **ソース**  
  
 \<ソース > 要素が 1 つのイメージのソース資産 (XAML および PNG) を定義します。  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|URI|[必須]イメージを読み込むことを定義する URI。 次のいずれかを指定できます。<br /><br /> は、 [Pack URI](http://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx)アプリケーションを使用して:///オーソリティ<br /><br /> -絶対コンポーネント リソース参照<br /><br /> -ネイティブ リソースを含むファイルへのパス|  
|背景|[省略可能]背景が使用するものでは、ソースの種類にどのようなことを示します。<br /><br /> 次のいずれかを指定できます。<br /><br /> - *Light*: 明るい背景では、ソースを使用できます。<br /><br /> - *濃い*: ソースは、暗い背景で使用できます。<br /><br /> - *ハイコントラスト*: ハイ コントラスト モードで任意のバック グラウンドでは、ソースを使用できます。<br /><br /> - *HighContrastLight*: ハイ コントラスト モードのライト バック グラウンドでは、ソースを使用できます。<br /><br /> -*HighContrastDark*: ソースは、ハイ コントラスト モードで暗い背景で使用できます。<br /><br /> 場合、**バック グラウンド**属性を省略すると、ソースは、任意の背景で使用できます。<br /><br /> 場合**バック グラウンド**は*Light*、*濃い*、 *HighContrastLight*、または*HighContrastDark*、ソースの色を反転ことはありません。 場合**バック グラウンド**を省略するかに設定*ハイコントラスト*、ソースの色の反転は、イメージのによって制御される**AllowColorInversion**属性。|  
  
 A\<ソース > 要素は省略可能な次のサブ要素の 1 つだけであることができます。  
  
||||  
|-|-|-|  
|**要素**|**属性 (必要なすべて)**|**定義**|  
|\<サイズ >|[値]|(デバイス単位) で指定されたサイズのイメージのソースが使用されます。 画像は正方形になります。|  
|\<SizeRange >|MinSize、MaxSize|ソースは、範囲 (デバイス単位) の最大サイズに MinSize からイメージに使用されます。 画像は正方形になります。|  
|\<ディメンション >|Width、Height|指定した幅と高さ (デバイス単位) のイメージのソースが使用されます。|  
|\<DimensionRange >|MinWidth、MinHeight、<br /><br /> MaxWidth、MaxHeight|ソースは、範囲 (デバイス単位) で最大の幅と高さを幅/高さの最小値からのイメージに使用されます。|  
  
 A\<ソース > 要素は省略可能なこともできます\<NativeResource > を定義するサブ要素を\<ソース > マネージ アセンブリではなく、ネイティブ アセンブリから読み込むことができます。  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|型|[必須]XAML または PNG のいずれかのネイティブのリソースの種類|  
|ID|[必須]ネイティブ リソースの整数 ID の部分|  
  
 **ImageList**  
  
 \<ImageList > 要素が 1 つのストリップに返すことができるイメージのコレクションを定義します。 ストリップは、必要に応じて、オンデマンドで構築されます。  
  
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
|外部|[省略可能、既定値は false]イメージ モニカーが現在のマニフェストでイメージを参照するかどうかを示します。|  
  
 含まれているイメージのモニカーを現在のマニフェストで定義されているイメージを参照する必要はありません。 イメージ ライブラリに含まれているイメージが見つからない場合、空のプレース ホルダー イメージは、代わりに使用されます。  
  
## <a name="how-to-use-the-tool"></a>ツールを使用する方法  
 **カスタム イメージのマニフェストの検証**  
  
 カスタム マニフェストを作成するには、マニフェストを自動生成を ManifestFromResources ツールを使用することをお勧めします。 カスタム マニフェストを検証するには、イメージ ライブラリ ビューアーを起動し、ファイルを選択 > パスの設定. ディレクトリの検索 ダイアログを開きます。 イメージのマニフェストを読み込む検索ディレクトリが使用されますが、それをも使用して、マニフェストでイメージを含む .dll ファイルを検索するようにしてこのダイアログ ボックスに、マニフェストと DLL のディレクトリの両方を含める。  
  
 ![イメージ ライブラリ ビューアーの検索](../../extensibility/internals/media/image-library-viewer-search.png "イメージ ライブラリ ビューアーの検索")  
  
 クリックして**を追加しています.** マニフェストと、対応する Dll を検索する新しい検索ディレクトリを選択します。 ツールには、これらの検索ディレクトリが記憶してし、をオンまたはオフにするディレクトリをオンまたはオフにすることができます。  
  
 既定では、このツールを Visual Studio のインストール ディレクトリを検索し、それらのディレクトリを検索ディレクトリの一覧に追加されます。 ツールを検索しないディレクトリを手動で追加することができます。  
  
 切り替えるツールを使用できるすべてのマニフェストが読み込まれると、**バック グラウンド**色、 **DPI**、**ハイ コントラスト**、または**ディザリングを行います**のイメージ、ユーザーは、さまざまな設定を正しくレンダリングされるされることを確認のイメージ アセットを調べることができます視覚的にできるようにします。  
  
 ![イメージ ライブラリ ビューアーの背景](../../extensibility/internals/media/image-library-viewer-background.png "イメージ ライブラリ ビューアーの背景")  
  
 背景色は、光、濃色、またはカスタム値を設定できます。 「カスタム色」を選択すると、色の選択 ダイアログを開くし、簡単な呼び出し後のバック グラウンドのコンボ ボックスの下部にそのカスタム色を追加します。  
  
 ![イメージ ライブラリ ビューアーのカスタム色](../../extensibility/internals/media/image-library-viewer-custom-color.png "イメージ ライブラリ ビューアーのカスタム色")  
  
 イメージのモニカーを選択すると、右側のイメージの詳細ペインでそのモニカーの背後にある各実際のイメージの情報が表示されます。 ウィンドウでは、名前または生の GUID:ID の値では、モニカーをコピーすることもできます。  
  
 ![イメージ ライブラリ ビューアーのイメージの詳細](../../extensibility/internals/media/image-library-viewer-image-details.png "イメージ ライブラリ ビューアーのイメージの詳細")  
  
 イメージ ソースごとに表示される情報テーマが適用されたことができるかどうか、上に表示するバック グラウンドの種類が含まれていますハイ コントラスト、それが有効で、どのようなサイズをサポートまたはサイズに依存しない、かどうかは、ネイティブ アセンブリからイメージを取得するかどうか  
  
 ![イメージ ライブラリ ビューアーできるテーマ](../../extensibility/internals/media/image-library-viewer-can-theme.png "イメージ ライブラリ ビューアーにテーマことができます")  
  
 イメージ マニフェストを検証するときに、マニフェストとイメージの実際の場所に DLL をデプロイすることをお勧めします。 これには、相対パスが正しく動作していると、イメージ ライブラリが見つけるし、マニフェストとイメージの DLL を読み込むことができますを確認します。  
  
 **イメージのカタログ KnownMonikers の検索**  
  
 Visual Studio スタイルに合わせて、Visual Studio 拡張機能は、Visual Studio のイメージのカタログではなく作成および使用して、独自のイメージを使用できます。 これは、それらのイメージを維持する必要があるという利点があります、Visual Studio をサポートするすべての DPI 設定で正しいなりますので、イメージが高 DPI のバックアップ イメージを持つことが保証されます。  
  
 イメージ ライブラリ ビューアーには、ユーザーがのイメージ アセットを表すモニカーを検索して、コード内でそのモニカーを使用できるように検索するマニフェストができます。 イメージを検索するには、検索ボックスに必要な検索語句を入力し、Enter キーを押します。 一致の数は見つかったイメージの合計から、マニフェストのすべての下部にあるステータス バーが表示されます。  
  
 ![イメージ ライブラリ ビューアーのフィルター](../../extensibility/internals/media/image-library-viewer-filter.png "イメージ ライブラリ ビューアーのフィルター")  
  
 既存のマニフェストでイメージ モニカーを検索するときに検索および、Visual Studio イメージ カタログのモニカーのみ、他の意図的にパブリックにアクセスできるモニカー、または独自のカスタム モニカーを使用することお勧めします。 非パブリックのモニカーを使用する場合カスタム UI が壊れることがありますか、イメージ変更された予期しない方法で場合、またはこれらの非パブリックのモニカーとイメージを変更または更新するとき。  
  
 さらに、GUID によって検索が可能です。 この種類の検索は、1 つのマニフェストにリストをフィルター処理に役立つまたはマニフェストの場合は、そのマニフェストの 1 つのサブセクションには、複数の Guid が含まれています。  
  
 ![イメージ ライブラリ ビューアーのフィルター GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "イメージ ライブラリ ビューアーのフィルター GUID")  
  
 最後に、ID で検索することも同様です。  
  
 ![イメージ ライブラリ ビューアーのフィルター ID](../../extensibility/internals/media/image-library-viewer-filter-id.png "イメージ ライブラリ ビューアーのフィルター ID")  
  
## <a name="notes"></a>メモ  
  
-   既定では、このツールは Visual Studio のインストール ディレクトリに存在するいくつかのイメージのマニフェストにプルします。 モニカーをパブリックに使用できるは 1 つだけが、 **Microsoft.VisualStudio.ImageCatalog**マニフェストします。 GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (は**いない**カスタム マニフェストにこの GUID を上書き) の種類: KnownMonikers  
  
-   ツールは、アプリケーションが、実際に表示するのに数秒がかかる場合がありますのでが見つかると、すべてのイメージ マニフェストを読み込むの起動時にしようとします。 低速または応答も、マニフェストの読み込み中にられます可能性があります。  
  
## <a name="sample-output"></a>出力例  
 このツールは、任意の出力を生成しません。

