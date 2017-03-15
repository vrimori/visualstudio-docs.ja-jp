---
title: "構文のカスタム エディターの色指定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - カスタム構文の色分け表示"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 構文のカスタム エディターの色指定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio SDK 環境のエディターはコア エディターを含む特定の構文の項目を識別し特定のドキュメントのビューの指定された色で表示する言語サービスを使用します。  
  
## 要件の色付け  
 言語サービスの colorizer を実装するすべてのエディターがあります :  
  
1.  colorized するテキストテキスト ドキュメントのビューを提供する <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> を実装するオブジェクトを管理するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> を実装するオブジェクトを使用します。  
  
2.  言語に関するサービスを識別する GUID を使用する VSPackage サービス プロバイダーを呼び出すことによって特定の言語サービスにインターフェイスを取得します。  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> を実装するオブジェクトの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> のメソッドを呼び出します。  このメソッドは colorized テキストを管理するにはVSPackage を使用する <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> の実装と言語サービスを関連付けます。  
  
## 言語サービスの Colorizer のコア エディターの使用  
 colorizer を持つ言語サービスはコア エディターのインスタンスを通じて取得された場合は言語サービスの colorizer してテキストを解析およびレンダリングはのそのほかの実行を必要とせずに自動的に行われます。  
  
 透過的に IDE:  
  
-   これは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> の実装で追加または変更されたと同様に必要 colorizer をテキストを解析および分析するために呼び出されます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> の実装によって提供されるドキュメント ビューが提供するが表示 colorizer によって返される情報を使用して更新され描画されることを確認します。  
  
## 言語サービスの主要 Colorizerエディターの使用  
 非主要エディターのインスタンスは言語サービスの構文の色づけサービスを使用できますが明示的に取得しサービスの colorizer を適用しドキュメントを再描画するために自身を表示します。  
  
 これを行うには主要エディターが必要です :  
  
1.  \(`T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> を実行する\) 言語サービスの colorizer オブジェクトを取得します。  VSPackage は言語サービスのインターフェイス <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> のメソッドを呼び出すことで実現されます。  
  
2.  テキストの特定の範囲が colorized 要求する <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> のメソッドを呼び出します。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> メソッドの戻り値colorized テキスト範囲の各文字に 1 の配列。  またコメントキーワードデータ型などの色設定可能項目の特定の型としてテキスト範囲を指定します。  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> によって返される情報テキストを再描画および表示に色づけを使用します。  
  
> [!NOTE]
>  言語サービスの colorizer の汎用 Visual Studio 環境 SDK のテキスト色指定機能を使用するために使用できるだけでなくVSPackage を選択できます。  この機能の詳細については[フォントおよび色を使用します。](../extensibility/using-fonts-and-colors.md) を参照してください。  
  
## 参照  
 [構文の色分けで従来の言語サービス](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [構文の色分けを実装します。](../extensibility/internals/implementing-syntax-coloring.md)   
 [方法: ビルトインの装飾が可能な項目を使用して](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [カスタムの装飾が可能な項目](../extensibility/internals/custom-colorable-items.md)