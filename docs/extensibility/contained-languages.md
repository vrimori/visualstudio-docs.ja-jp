---
title: "格納されている言語 | Microsoft Docs"
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
  - "エディター [Visual Studio SDK] レガシー - には、言語が含まれています。"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 格納されている言語
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*含まれる言語は* 他の言語に含まれる言語です。  たとえば[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] のページの HTML が [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] または [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] のスクリプトが含まれる可能性があります。  複数言語のアーキテクチャは.aspx ファイルではHTML エディターおよびスクリプト言語の両方に IntelliSense 色づけなどの編集機能を提供することが必要になります。  
  
## 実装  
 に含まれる言語に対して実行する必要がある最も重要なインターフェイスが <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> のインターフェイスです。  このインターフェイスは主言語内でホストできる言語によって実装されます。  これは言語サービスの colorizerテキスト ビュー フィルターPRIMARY LANGUAGE ID のサービスにアクセスできます。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> は <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> のインターフェイスを作成することができます。  次の手順では含まれている言語の実装方法を示します :  
  
1.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> の言語サービス ID とインターフェイス ID を取得するに `QueryService()` を使用します。  
  
2.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> のインターフェイスを作成するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> のメソッドを呼び出します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>項目のインターフェイス ID \(<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL><xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>または <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION> の一つ以上\) と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> のインターフェイスを渡します。  
  
3.  テキスト バッファーのコーディネーターのオブジェクトである <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> のインターフェイスはその言語のバッファーにプライマリ ファイル内の位置をマップするために必要な基本的なサービスが用意されています。  
  
     たとえば一つの .aspx ファイルにプライマリ ファイルはASP ファイルHTMLおよび含まれるすべてのコードを追加します。  ただしセカンダリ バッファーはクラス定義とともにそのバッファーに有効なコード ファイルを再生するに含まれるコードが含まれています。  バッファーのコーディネーターは1 バイトのバッファーから他方に調整の編集機能を処理します。  
  
4.  PRIMARY LANGUAGE である <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> のメソッドはバッファー内のテキストの内容が 2 バッファーの対応するテキストにマップされるかバッファーのコーディネーターに指示します。  
  
     主キーおよび言語は現在の範囲を含まない <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> の構造体の配列を渡します。  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> のメソッドと <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> のメソッドはからのバッファーにマッピングをその逆も提供します。