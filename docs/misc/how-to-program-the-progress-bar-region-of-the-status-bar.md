---
title: "方法: ステータス バーの進行状況バー領域をプログラミングする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ステータス バー、進行状況バー領域"
  - "進行状況バー、ステータス バー"
  - "ステータス バー、プログラミング"
ms.assetid: 4b54616a-8c20-436d-b764-f2380e5760f2
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 方法: ステータス バーの進行状況バー領域をプログラミングする
たとえば [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ステータス バーのプログレス バーの領域はファイルをディスクに保存する簡単な段階的な操作の進行状況が表示されます。  
  
### Visual Studio のステータス バーのプログレス バーの領域を使用します。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> サービスで使用できる <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> のインターフェイスのインスタンスを取得します。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> のメソッドを呼び出して開始値にプログレス バーを初期化します。  
  
3.  新しい値を設定するには操作が <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> のメソッドを使用して続行にプログレス バーを更新します。  
  
## 使用例  
 この例ではプログレス バーを初期化更新する方法を示します。  
  
 [!CODE [VSSDKProgressStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkprogressstatusbar#1)]  
  
 例ではコード :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> サービスから <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> のインターフェイスのインスタンスを取得します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> のメソッドを呼び出してプログレス バーの開始値を初期化します。  
  
-   `for` のループを反復処理すると <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> のメソッドを使用してプログレス バーの値を更新してをシミュレートします。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> のメソッドを使用してプログレス バーをオフにします。  
  
## 参照  
 [ステータス バーの拡張](../extensibility/extending-the-status-bar.md)   
 [方法: ステータス バーのフィードバック領域に対する読み取りと書き込み](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [方法: ステータス バーのアニメーションの領域を使用する](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [方法: ステータス バーのデザイナーの領域をプログラミングする](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)