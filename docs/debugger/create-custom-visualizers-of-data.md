---
title: カスタム データ ビジュアライザーを作成する |Microsoft Docs
ms.date: 11/07/2018
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
ms.openlocfilehash: 9bb693e509eb12b01d3c70f8f341b39de06e5797
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54204389"
---
# <a name="create-custom-data-visualizers"></a>カスタム データ ビジュアライザーを作成します。
 A*ビジュアライザー*の一部である、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]デバッガー ユーザー インターフェイスのデータ型に適した方法で変数またはオブジェクトを表示します。 たとえば、HTML ビジュアライザーは、HTML 文字列を解釈し、ブラウザー ウィンドウに表示される結果を表示します。 ビットマップ ビジュアライザーは、ビットマップ構造を解釈し、表すグラフィックを表示します。 一部のビジュアライザーを使用して、変更も、データを表示できます。

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] デバッガーには、6 つの標準的なビジュアライザーが用意されています。 テキスト、HTML、XML、および JSON ビジュアライザーが文字列オブジェクトで動作します。 WPF ツリー ビジュアライザーには、WPF オブジェクトのビジュアル ツリーのプロパティが表示されます。 データセット visualizer は、データセット、データ ビュー、および DataTable オブジェクトによって適しています。 

ビジュアライザーの詳細については、Microsoft、サード パーティ、およびコミュニティからダウンロードできる場合があります。 独自のビジュアライザーを記述してをインストールすることができます、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]デバッガー。

デバッガーで、ビジュアライザーは虫眼鏡のアイコンで表される![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")します。 アイコンを選択することができます、**データヒント**、デバッガー**ウォッチ**ウィンドウ、または **[クイック ウォッチ]** ダイアログ ボックスで、し、対応するオブジェクトの適切なビジュアライザーを選択します。

## <a name="write-custom-visualizers"></a>カスタム ビジュアライザーを記述します。

 > [!NOTE]
 > ネイティブ コードに対するカスタム ビジュアライザーを作成するを参照してください。、 [SQLite ネイティブ デバッガー ビジュアライザー](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer)サンプル。 UWP と Windows 8.x アプリでは、カスタム ビジュアライザーはサポートされていません。

<xref:System.Object> および <xref:System.Array> を除く任意のマネージド クラスのオブジェクトのカスタム ビジュアライザーを記述できます。  
  
デバッガー ビジュアライザーのアーキテクチャには、次の 2 つの部分があります。  
  
- *デバッガー側*Visual Studio デバッガー内で実行し、作成し、ビジュアライザーのユーザー インターフェイスが表示されます。  
  
- "*デバッグ対象側*" - Visual Studio がデバッグしているプロセス (*デバッグ対象*) 内で動作します。 デバッグ対象プロセスに (たとえば、文字列オブジェクト) を視覚化するデータ オブジェクトが存在します。 デバッグ対象側は、オブジェクトを作成するユーザー インターフェイスに表示されるデバッガー側に送信します。  

デバッガー側からのデータ オブジェクトを受け取る、*オブジェクト プロバイダー*を実装する、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>インターフェイス。 デバッグ対象側を使用してオブジェクトを送信する、*オブジェクト ソース*から派生<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>します。 

オブジェクト プロバイダーは、データをバックアップできるようにデータを編集できるビジュアライザーを記述するオブジェクト ソースにも送信できます。 式エバリュエーターとオブジェクト ソースと対話するオブジェクト プロバイダーをオーバーライドするとします。  
  
デバッグ対象側とデバッガー側がを通じて相互に通信<xref:System.IO.Stream>にデータをシリアル化するメソッドがオブジェクトを<xref:System.IO.Stream>および逆シリアル化、<xref:System.IO.Stream>データ オブジェクトにします。  

型がオープン型である場合にのみ、ジェネリック型のビジュアライザーを記述できます。 この制限は、`DebuggerTypeProxy` 属性を使用する場合の制限と同じです。 詳細については、次を参照してください。 [DebuggerTypeProxy 属性の使用](../debugger/using-debuggertypeproxy-attribute.md)します。  
  
カスタムのビジュアライザーでは、セキュリティについての配慮が必要な場合があります。 参照してください[ビジュアライザーのセキュリティに関する考慮事項](../debugger/visualizer-security-considerations.md)します。  
  
次の手順では、ビジュアライザーの作成の概要を提供します。 詳細については、次を参照してください。[チュートリアル: で、ビジュアライザーを記述C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)または[チュートリアル: Visual Basic でビジュアライザーを記述](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)します。  
  
### <a name="to-create-the-debugger-side"></a>デバッガー側を作成するには  
  
継承するクラスを作成するをデバッガー側のビジュアライザーのユーザー インターフェイスを作成する<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>、上書き、<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>インターフェイスを表示するメソッド。 使用することができます<xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>ビジュアライザーに Windows フォーム、ダイアログ、およびコントロールを表示します。  
  
1.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> メソッドを使用して、視覚化するオブジェクトをデバッガー側で取得します。  
  
1.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> を継承するクラスを作成します。  
  
1.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> メソッドをオーバーライドしてインターフェイスを表示します。 使用<xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>インターフェイスで Windows フォーム、ダイアログ、およびコントロールを表示するメソッド。  
  
4.  適用<xref:System.Diagnostics.DebuggerVisualizerAttribute>、表示するビジュアライザーを付けます (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)。  
  
### <a name="to-create-the-debuggee-side"></a>デバッグ対象側を作成するには  
  
デバッグ対象側のコードを使用して指定する、<xref:System.Diagnostics.DebuggerVisualizerAttribute>します。  
  
1.  <xref:System.Diagnostics.DebuggerVisualizerAttribute> をビジュアライザー (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) とオブジェクト ソース (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) に適用します。 オブジェクトのソースを省略した場合、ビジュアライザーは既定のオブジェクト ソースを使用します。  
  
1.  ビジュアライザーの編集もデータ オブジェクトを表示させるには、オーバーライド、`TransferData`または`CreateReplacementObject`メソッドから<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>します。   
  
## <a name="see-also"></a>関連項目
  
 [チュートリアル: C# でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [チュートリアル: Visual Basic でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [方法: ビジュアライザーをインストールする](../debugger/how-to-install-a-visualizer.md)  
  
 [方法: ビジュアライザーをテストおよびデバッグする](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [ビジュアライザー API リファレンス](../debugger/visualizer-api-reference.md)  
  
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)