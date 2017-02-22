---
title: "方法: エラー マーカーを実装します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - エラー マーカー"
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: エラー マーカーを実装します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エラーのマーカー \(赤い波線\) 実行しテキスト エディターをカスタマイズすることは困難です。  ただしVSPackage のユーザーに提供する利点はその情報を提供するコストが打ち消される可能性があります。  エラーのマーカーがわずかに言語パーサーが squiggly または下に赤い線が正しくテキストと見なされることを示します。  この問題によって不適切なコードを表示することでプログラマができます。  
  
 赤い波線を実行するにはテキスト マーカーを使用します。  通常言語サービスはアイドル時またはバックグラウンド スレッドでバックグラウンド パスとしてテキスト バッファーに赤い波線を追加します。  
  
### 赤い波線の機能を実装します。  
  
1.  目的の場所で赤い波線するテキストを選択します。  
  
2.  型 `MARKER_CODESENSE_ERROR` マーカーを作成します。  詳細については、「[方法: 標準のテキストのマーカーを追加](../extensibility/how-to-add-standard-text-markers.md)」を参照してください。  
  
3.  その後<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイス ポインターを渡します。  
  
 このプロセスを使用して特定のツールヒント テキスト マーカーの上や特別なコンテキスト メニューを作成します。  詳細については、「[方法: 標準のテキストのマーカーを追加](../extensibility/how-to-add-standard-text-markers.md)」を参照してください。  
  
 次のオブジェクトにはエラーのマーカーを表示する前に必要です。  
  
-   パーサー。  
  
-   再分析する行を識別するために行情報の変更のレコードを保持するタスクのプロバイダー \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> の実装\)。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>\) メソッドを使用してビューからキャレットのイベントのフィルターを変更キャプチャテキストビュー。  
  
 パーサータスクはエラー プロバイダーとフィルターのマーカーを可能にするために必要なインフラストラクチャを提供します。  次の手順ではエラーのマーカーを表示するプロセスを提供します。  
  
1.  フィルター処理ビューでビューのデータに関連するタスクのプロバイダーへのポインターを取得します。  
  
    > [!NOTE]
    >  メソッドのツールヒントにエラー記号など同じコマンドのフィルターステートメント入力候補使用できます。  
  
2.  別の行に移動したことを示すフィルターがイベントを受け取るとタスクはエラーをチェックするように作成されます。  
  
3.  タスク ハンドラーは行が汚れているチェックします。  その場合はエラーの行を解析します。  
  
4.  エラーが発生した場合タスクのプロバイダーはタスク項目のインスタンスを作成します。  このインスタンスは環境がテキスト ビューでエラーのマーカーとして使用するテキスト マーカーを作成します。  
  
## 参照  
 [レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキストのマーカーを追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: カスタム テキスト マーカーを作成](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: テキストのマーカーを使用します。](../extensibility/how-to-use-text-markers.md)