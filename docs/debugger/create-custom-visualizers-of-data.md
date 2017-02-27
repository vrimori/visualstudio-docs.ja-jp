---
title: "ビジュアライザー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.visualizer.troubleshoot"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッガー, ビジュアライザー"
  - "ビジュアライザー"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# ビジュアライザー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ビジュアライザーは、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] デバッガー ユーザー インターフェイスのコンポーネントです。  *ビジュアライザー*は、ダイアログ ボックスまたはその他のインターフェイスを作成して、データ型に適した方法で変数またはオブジェクトを表示します。  たとえば、HTML ビジュアライザーは、HTML 文字列を解釈し、ブラウザー ウィンドウに表示されるとおりに結果を表示します。また、ビットマップ ビジュアライザーは、ビットマップ構造体を解釈し、ビットマップが表すグラフィックを表示します。  一部のビジュアライザーでは、データを表示するだけでなく、変更することもできます。  
  
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] デバッガーには、6 つの標準的なビジュアライザーが用意されています。  テキスト ビジュアライザー、HTML ビジュアライザー、XML ビジュアライザー、JSON ビジュアライザー: これらのすべてが文字列オブジェクトを処理します。WPF ツリー ビジュアライザー: WPF オブジェクトのビジュアル ツリーのプロパティを表示します。データセット ビジュアライザー: DataSet オブジェクト、DataView オブジェクト、および DataTable オブジェクトを処理します。  その他のビジュアライザーは、今後 Microsoft Corporation からダウンロード可能になる場合があり、サード パーティやコミュニティからも入手できます。  また、独自のビジュアライザーを記述して、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] デバッガーにインストールすることもできます。  
  
> [!NOTE]
>  **ストア** アプリでは、標準的なテキスト、HTML、XML、および JSON ビジュアライザーがサポートされています。  カスタム \(ユーザーが作成した\) ビジュアライザーはサポートされていません。  
  
 デバッガーでは、ビジュアライザーは虫眼鏡アイコンで表されます。  デバッガー変数ウィンドウまたは **\[クイック ウォッチ\]** ダイアログ ボックスの **\[データヒント\]** に虫眼鏡アイコンが表示されている場合、この虫眼鏡をクリックすると、対応するオブジェクトのデータ型に適したビジュアライザーを選択できます。  
  
 ビジュアライザーは、.NET Compact Framework ではサポートされていません。  
  
> [!NOTE]
>  デバッガー ビジュアライザーでは、部分信頼アプリケーションが許可する以上の特権が必要です。  この結果、部分信頼コードで動作が停止した場合、ビジュアライザーは読み込まれません。  ビジュアライザーを使用してデバッグするには、完全信頼コードを実行する必要があります。  
  
## このセクションの内容  
 [方法 : ビジュアライザーを記述する](../debugger/how-to-write-a-visualizer.md)  
  
 [チュートリアル : C\# でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [方法 : ビジュアライザーをインストールする](../debugger/how-to-install-a-visualizer.md)  
  
 [方法 : ビジュアライザーをテストおよびデバッグする](../Topic/How%20to:%20Test%20and%20Debug%20a%20Visualizer.md)  
  
 [ビジュアライザー API リファレンス](../debugger/visualizer-api-reference.md)  
  
## 関連項目  
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)