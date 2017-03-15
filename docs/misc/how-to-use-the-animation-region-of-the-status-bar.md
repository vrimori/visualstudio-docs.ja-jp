---
title: "方法: ステータス バーのアニメーションの領域を使用する | Microsoft Docs"
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
  - "ステータス バー、プログラミング"
  - "ステータス バー、アニメーションの領域"
  - "アニメーションの領域、ステータス バー"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 方法: ステータス バーのアニメーションの領域を使用する
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ステータス バーの領域が不定長さのかかる操作または操作を示すループ   アニメーションを表示します \(たとえばソリューション内の複数のプロジェクトをビルド\)。  
  
### Visual Studio のステータス バーの領域を使用します。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> サービスで使用できる <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> のインターフェイスのインスタンスを取得します。  
  
2.  ステータス バーの <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> のメソッドを呼び出してアニメーションを開始します。  最初のパラメーターの値として 12 番目のパラメーターの値としてアニメーション化されるアイコンへの参照を渡します。  
  
3.  ステータス バーの <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> のメソッドを呼び出してアニメーションを停止します。  最初のパラメーターの値として 02 番目のパラメーターの値としてアニメーション化されるアイコンへの参照を渡します。  
  
## 使用例  
 この例ではアニメーションの領域の組み込みアニメーションを実行する方法を示します。  
  
 [!CODE [VSSDKAnimationStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkanimationstatusbar#1)]  
  
## 参照  
 [ステータス バーの拡張](../extensibility/extending-the-status-bar.md)   
 [方法: ステータス バーのフィードバック領域に対する読み取りと書き込み](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [方法: ステータス バーの進行状況バー領域をプログラミングする](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [方法: ステータス バーのデザイナーの領域をプログラミングする](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)