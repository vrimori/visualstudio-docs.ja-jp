---
title: "ドロップダウン バー | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシ - ドロップダウン バー"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ドロップダウン バー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ドロップダウン バーはコード ウィンドウの上部に提供され2 個のドロップダウン リストが含まれています。  
  
## ドロップ ダウン バーのインターフェイス  
 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] ではドロップダウン バーは次の図に示すように [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] の項目と [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 項目のメンバー関数のリストが含まれます。  
  
 ![ドロップダウン バー](../extensibility/media/vsdropdown_bar.gif "vsDropdown\_bar")  
ドロップ ダウン バー  
  
 ドロップダウン バーを実行すると主要な重要度 4 のインターフェイスがあります :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     ドロップダウン バーの内容を挿入するにはこのインターフェイスを実装します。  それぞれのドロップダウン組み合わせはプレーンテキストまたは豪華なテキスト \(太字斜体下線\) を含めることができますがウィンドウのテキストのフォントの色指定を灰色のフォントの色指定されドロップダウン項目の横に応じて小さいビットマップを指定できます。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> インターフェイスビットマップ イメージと同様にイメージ リストで指定します。  それぞれのドロップダウン リストと別のイメージを指定できます。; ただし各イメージ リストは同じ高さのイメージを含める必要があります。  また<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> のメソッドを使用して各組み合わせにヒントを提供できます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     このインターフェイスを作成または破棄します。コード ウィンドウのドロップダウン バーを呼び出します。  このインターフェイスがドロップダウン バーがコード ウィンドウに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> のメソッドを呼び出して既にアタッチされているかどうかを確認するために使用できます。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> から <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> の呼び出し <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     ドロップダウン バーと直接通信するにはこのインターフェイスを呼び出します。  ドロップダウン バーのコンテンツの更新を強制するかリスト ボックスの 1 種類の選択を変更するにはこのインターフェイスを使用できます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     言語サービスのレジストリ キーの `ShowDropdownBarOption` を登録した場合はコード ウィンドウ マネージャーはドロップダウン バーを表示するかどうかをユーザー設定に関する同期するにはこのイベントを監視する必要があります。  言語サービスのキーはこのオプションを登録しないとドロップダウン バーを表示または非表示にするオプションは\[入力\] メニューの ENT0ENT 無効になります。  
  
## コード ウィンドウにドロップダウン バーのアタッチ  
 作成したコード ウィンドウにドロップダウン バーをアタッチするには言語サービスはドロップダウン バーに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> のメソッドが呼び出されたときにアタッチする必要があります。  ドロップダウン バーがまだ存在しないことを <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> メソッドの呼び出しが示している場合 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> を呼び出します。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> の実装がアタッチされたときに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> のインターフェイスにアクセスするには<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> のポインターからの呼び出し <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> はに戻ります。  
  
## 参照  
 [レガシ API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [従来の言語サービス内のナビゲーション バーのサポート](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)