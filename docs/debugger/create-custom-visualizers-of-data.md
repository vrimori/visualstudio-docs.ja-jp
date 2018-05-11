---
title: データのカスタム ビジュアライザーを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2a1602808cb21bd247d2bb1d249ab7ddea81524
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-visualizers-of-data"></a>データのカスタム ビジュアライザーを作成します。
 ビジュアライザーのコンポーネントである、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]デバッガー ユーザー インターフェイス。 A*ビジュアライザー*  ダイアログ ボックスまたはそのデータ型に適切な方法で変数またはオブジェクトを表示する別のインターフェイスを作成します。 たとえば、HTML ビジュアライザーは、HTML 文字列を解釈し、ブラウザー ウィンドウに表示されるとおりに結果を表示します。また、ビットマップ ビジュアライザーは、ビットマップ構造体を解釈し、ビットマップが表すグラフィックを表示します。 一部のビジュアライザーでは、データを表示するだけでなく、変更することもできます。

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] デバッガーには、6 つの標準的なビジュアライザーが用意されています。 これらは、テキスト、HTML、XML、および JSON ビジュアライザー、文字列オブジェクトのうちすべての作業WPF オブジェクトのビジュアル ツリー; のプロパティを表示するため、WPF ツリー ビジュアライザーで、データセット ビジュアライザー: DataSet、DataView、DataTable オブジェクトに対して機能します。 その他のビジュアライザーは、今後 Microsoft Corporation からダウンロード可能になる場合があり、サード パーティやコミュニティからも入手できます。 また、独自のビジュアライザーを記述して、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] デバッガーにインストールすることもできます。

 > [!NOTE]
 > ネイティブ コードに対するカスタム ビジュアライザーを作成するを参照してください。、 [SQLite ネイティブ デバッガー ビジュアライザー](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer)サンプルです。 UWP アプリと Windows 8.x アプリでのカスタム ビジュアライザーはサポートされていません。

 デバッガーでは、ビジュアライザーは虫眼鏡のアイコンで表されます![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")です。 虫眼鏡のアイコンが表示される、**データヒント**と同様に、デバッガー ウィンドウで、**ウォッチ**ウィンドウ、または、 **[クイック ウォッチ]** ダイアログ ボックスで、虫眼鏡をクリックすることができます対応するオブジェクトのデータ型に適したビジュアライザーを選択します。

## <a name="overview-of-custom-visualizers"></a>カスタム ビジュアライザーの概要

<xref:System.Object> および <xref:System.Array> を除く任意のマネージ クラスのオブジェクトのカスタム ビジュアライザーを記述できます。  
  
 デバッガー ビジュアライザーのアーキテクチャには、次の 2 つの部分があります。  
  
-   *デバッガー側*Visual Studio デバッガー内で実行されます。 デバッガー側のコードは、ビジュアライザーのユーザー インターフェイスを作成し、表示します。  
  
-   *デバッグ対象側*Visual Studio がデバッグ プロセス内で実行 (、*デバッグ対象*)。  
  
 視覚化するデータ オブジェクト (String オブジェクトなど) は、デバッグ対象プロセスに存在します。 このためデバッグ対象側では、そのデータ オブジェクトをデバッガー側に送る必要があります。これによって、デバッガー側では、作成したユーザー インターフェイスを使ってデータ オブジェクトを表示できるようになります。  
  
 デバッガー側から、視覚化するのには、このデータ オブジェクトを受け取る、*オブジェクト プロバイダー*を実装する、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>インターフェイスです。 デバッグ対象側に送信、データ オブジェクトを通じて、*オブジェクト ソース*から派生した<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>です。 オブジェクト プロバイダーは、オブジェクト ソースにデータを戻すこともできます。このため、データの表示だけでなく編集もできるビジュアライザーを記述できます。 オブジェクト プロバイダーは、式エバリュエーターと通信することでオブジェクト ソースと通信するようにオーバーライドできます。  
  
 デバッグ対象側とデバッガー側は、<xref:System.IO.Stream> を介して相互に通信します。 データ オブジェクトを <xref:System.IO.Stream> にシリアル化し、<xref:System.IO.Stream> をデータ オブジェクトに逆シリアル化するメソッドが用意されています。  
  
 デバッグ対象側のコードは、DebuggerVisualizer 属性 (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) で指定します。  
  
 デバッガー側でビジュアライザー ユーザー インターフェイスを作成するには、<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> を継承するクラスを作成し、<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> メソッドをオーバーライドしてインターフェイスを表示する必要があります。  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> を使用すると、Windows フォーム、ダイアログ、およびコントロールをビジュアライザーによって表示できます。  
  
 ジェネリック型のサポートは制限されています。 ジェネリック型がオープン型の場合にのみ、そのジェネリック型のビジュアライザーを記述できます。 この制限は、`DebuggerTypeProxy` 属性を使用する場合の制限と同じです。 詳細については、「 [DebuggerTypeProxy 属性を使用して](../debugger/using-debuggertypeproxy-attribute.md)です。  
  
 カスタムのビジュアライザーでは、セキュリティについての配慮が必要な場合があります。 参照してください[ビジュアライザーのセキュリティに関する考慮事項](../debugger/visualizer-security-considerations.md)です。  
  
 以下の手順は、ビジュアライザーの作成に必要な作業の概要を示したものです。 詳細については、次を参照してください。[チュートリアル: c# でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)です。  
  
### <a name="to-create-the-debugger-side"></a>デバッガー側を作成するには  
  
1.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> メソッドを使用して、視覚化するオブジェクトをデバッガー側で取得します。  
  
2.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> を継承するクラスを作成します。  
  
3.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> メソッドをオーバーライドしてインターフェイスを表示します。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> メソッドを使用して、Windows フォーム、ダイアログ、およびコントロールをインターフェイスの一部として表示します。  
  
4.  <xref:System.Diagnostics.DebuggerVisualizerAttribute> をビジュアライザー (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) に適用します。  
  
### <a name="to-create-the-debuggee-side"></a>デバッグ対象側を作成するには  
  
1.  <xref:System.Diagnostics.DebuggerVisualizerAttribute> をビジュアライザー (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) とオブジェクト ソース (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) に適用します。 オブジェクト ソースを省略すると、既定のオブジェクト ソースが使用されます。  
  
2.  ビジュアライザーでデータ オブジェクトを表示するだけでなく、編集できるようにする場合は、`TransferData` の `CreateReplacementObject` メソッドまたは <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> メソッドをオーバーライドする必要があります。   
  
## <a name="in-this-section"></a>このセクションの内容
  
 [チュートリアル : C# でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [チュートリアル : Visual Basic でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [方法 : ビジュアライザーをインストールする](../debugger/how-to-install-a-visualizer.md)  
  
 [方法 : ビジュアライザーをテストおよびデバッグする](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [ビジュアライザー API リファレンス](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)