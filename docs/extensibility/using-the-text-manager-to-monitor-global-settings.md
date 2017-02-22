---
title: "グローバル設定を監視するためのテキスト マネージャーの使用 | Microsoft Docs"
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
  - "エディター [Visual Studio SDK] の従来のグローバル設定を監視します。"
  - "エディター [Visual Studio SDK] レガシー - テキスト マネージャー"
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# グローバル設定を監視するためのテキスト マネージャーの使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コア エディターを実装するとこれらの変更がエディターのインスタンスに影響する可能性があるためグローバル設定に対する変更を監視する必要があります。  待機してテキスト マネージャーが発生させたイベントに対する変更を追跡できます。  たとえばコア エディターでコンポーネントの外観と動作にグローバル設定をドキュメント データ オブジェクトなどテキスト ストアこのマネージャーの情報を指定し影響を受けるすべてのクライアントと通信します。  
  
## テキスト マネージャーの関数  
 テキスト マネージャーは次のような多数の設定のイベントを発生させる :  
  
-   バッファーはソース・コード管理下にあるかどうか  
  
-   ファイル変更通知用に登録する方法  
  
-   追跡する方法ビューが特定のバッファーに関連付けられた  
  
-   テキストの色づけの設定  
  
-   空白とタブの設定  
  
 特定の言語に固有の設定はマネージャーによってマネージ実行されません。  これらの設定は各言語サービスで管理する必要があります。  
  
 テキスト マネージャーのイベント通知は <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> のインターフェイスによって提供されます。  イベントを処理するためにクライアント オブジェクトこのインターフェイスを育てましたテキスト マネージャーを実行します。  これらのイベントのテキスト マネージャーの <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> インターフェイスを使用して登録します。  
  
## 参照  
 [コア エディターの内部](../extensibility/inside-the-core-editor.md)   
 [Editor Features](http://msdn.microsoft.com/ja-jp/bdac940d-1f14-4019-a01f-fd0bb3dc7198)