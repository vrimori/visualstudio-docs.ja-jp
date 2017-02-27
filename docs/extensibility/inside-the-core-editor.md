---
title: "コア エディターの内部 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - コア エディター"
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# コア エディターの内部
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコア エディターはテキスト情報を変更してクエリを可能にする複数のコンポーネントです。  レガシ API を使用してコア エディターをカスタマイズしてエディター アダプター経由でこれらのカスタマイズを使用し続けることができます。  新しいエディターの API にカスタマイズを使用することをお勧めします。  
  
 次の領域はコア エディターの重要な側面です :  
  
-   テキスト バッファー  
  
-   テキスト ビュー  
  
-   コード ウィンドウ  
  
-   テキスト マーカー  
  
-   テキスト マネージャー  
  
-   言語サービスとの統合  
  
## このセクションの内容  
 [レガシ API を使用してコア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 コア エディターを <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> のインスタンスを作成する方法の詳細な手順について説明します。  
  
 [レガシ API を使用してテキスト バッファーにアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 コア エディターのテキスト バッファーの役割についてバッファーにアクセスする方法とテキスト バッファーの <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクトによって実装されるインターフェイスのリストが関連付けられているシステムを提供します。  
  
 [レガシ API でのテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 テキスト バッファーのイベント通知に使用されるインターフェイスの一覧を示します。  
  
 [方法: テキスト バッファーのイベント、レガシ API の登録](../Topic/How%20to:%20Register%20for%20Text%20Buffer%20Events%20with%20the%20Legacy%20API.md)  
 テキスト バッファーのイベントに指示する方法について説明します。  
  
 [グローバル設定を監視するためのテキスト マネージャーの使用](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 コア エディターのコンポーネントによってグローバル設定で情報を共有するにはテキスト マネージャーとテキスト マネージャーのイベントの通知を受け取る方法がどのように使用されるかについて説明します。  
  
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 コア エディターのテキスト ビュー ロールについて説明し<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> のオブジェクトによって実装されるインターフェイスの一覧です。  
  
 [レガシ API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 コード ウィンドウに装飾を提供するためにコード ウィンドウ マネージャーを使用して指定する新しいビューについて通知します。テキスト ビューを囲むにはコード ウィンドウの使用される情報について説明します。  
  
 [レガシ API を使用してビューの設定を変更します。](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 ビューの設定を変換する方法および強制設定を削除する方法の詳細な手順について説明します。  
  
 [言語サービスとコア エディター](../extensibility/language-services-and-the-core-editor.md)  
 制御コードの装飾言語サービスのインスタンス化について説明します。  
  
## 関連項目  
 [チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録します。](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 マネージ コードのコア エディターを起動する方法の詳細な手順について説明します。  
  
 [ドロップダウン バー](../extensibility/drop-down-bar.md)  
 ドロップダウン バーがコード ウィンドウでを使用する話し合いドロップダウン バーの実行時に使用するインターフェイスについて説明します。  
  
 [レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)  
 これらはコア エディターでを使用する方法とテキスト マーカーを表示および管理するためのインターフェイスを一覧表示するテキスト マーカーの概念を示します。  
  
 [方法: 標準のテキストのマーカーを追加](../extensibility/how-to-add-standard-text-markers.md)  
 テキスト マーカーを作成する方法とショートカット メニューにカスタム コマンドを追加する方法の詳細な手順について説明します。  
  
 [方法: カスタム テキスト マーカーを作成](../extensibility/how-to-create-custom-text-markers.md)  
 カスタム テキスト マーカーを作成する方法およびサービスとしてマーカーの種類を指定する方法の詳細な手順について説明します。