---
title: "従来の言語サービスのコマンドを受信 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "言語サービスをインターセプトするコマンド"
  - "コマンドをインターセプトする言語サービス"
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 従来の言語サービスのコマンドを受信
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を使用するとテキスト ビューは処理するコマンドが傍受言語サービスを使用できます。  これはテキスト ビューを管理する言語固有の動作に便利です。  言語サービスのテキスト ビューに一つ以上のコマンドのフィルターを追加することでこれらのコマンドを受け取ることができます。  
  
## コマンドを取得し転送します  
 コマンドのフィルターは <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のオブジェクト。モニターの特定の文字シーケンスまたはショートカット キーです。  単一のテキスト ビューに複数のコマンドのフィルターを関連付けることができます。  各テキスト ビュー フィルターは系統コマンドを保持します。  新しいコマンドのフィルターを作成した後適切なテキスト ビューのチェーンにフィルターを追加します。  
  
 フィルター チェーンにコマンドを追加するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> の <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> のメソッドを呼び出します。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> を呼び出すと[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はコマンドのフィルターが処理されないコマンドを渡すことができる別のコマンドのフィルターを返します。  
  
 コマンドを処理するための次のオプションがあります :  
  
-   コマンドを処理しチェーン内の次のコマンドのフィルターに渡します。  
  
-   コマンドを処理し次のコマンドのフィルターに渡さないでください。  
  
-   コマンドを処理しないでください。ただし次のコマンドのフィルターに渡します。  
  
-   コマンドを無視します。  現在のフィルターで処理されること次のフィルターに渡さないでください。  
  
 方法の詳細についてのコマンドを処理する言語サービスが必要であるか[言語サービスのフィルターの重要なコマンド](../../extensibility/internals/important-commands-for-language-service-filters.md) を参照してください。