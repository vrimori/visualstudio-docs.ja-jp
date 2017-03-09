---
title: "方法: ステータス バーのフィードバック領域に対する読み取りと書き込み | Microsoft Docs"
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
  - "フィードバック領域、ステータス バー"
  - "ステータス バー、フィードバック領域"
  - "ステータス バー、概要"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 方法: ステータス バーのフィードバック領域に対する読み取りと書き込み
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のステータス バーにフィードバックの領域はショートサーキット メッセージを送信します。  テキスト表示の静的テキストを設定および取得し表示テキストを強調表示します。  
  
### Visual Studio のステータス バーの情報領域を使用するには  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> サービスで使用できる <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> のインターフェイスのインスタンスを取得します。  
  
2.  ステータス バーが <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> のインスタンスのことを <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> のメソッドを呼び出しているかどうかを確認します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A> のメソッドを呼び出し文字列を渡すことによりフィードバックの領域のテキストを設定します。  
  
4.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> のメソッドを呼び出してフィードバックの領域のテキストを読み取ります。  
  
## 使用例  
 この例ではテキストを書き込むフィードバックの領域でのテキストを読み取る方法を示します。  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 上の例では次のことを実行します :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> サービスから <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> のインターフェイスのインスタンスを取得します。  
  
-   ステータス バーが <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> のメソッドを呼び出しているかどうかを確認します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> のメソッドを呼び出してステータス バーにそのほかの更新プログラムを禁じます。  
  
-   ステータス バーのテキストを <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> のメソッドを呼び出して読み取りメッセージ ボックスに表示します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> を呼び出しパラメーターの 0 を渡すことによってステータス バーへの割り当てを更新します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> のメソッドを呼び出してステータス バーの内容を消去します。  
  
## 参照  
 [ステータス バーの拡張](../extensibility/extending-the-status-bar.md)   
 [方法: ステータス バーの進行状況バー領域をプログラミングする](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [方法: ステータス バーのアニメーションの領域を使用する](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [方法: ステータス バーのデザイナーの領域をプログラミングする](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)