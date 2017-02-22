---
title: "方法: 検索の実装とメカニズムを置換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] の従来の検索し、置換"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: 検索の実装とメカニズムを置換
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio に検索または置換を実行する 2 とおりの方法を示します。  1 番目の方法はシェルにテキストのイメージを渡すとその文字列の検索強調表示および置換を処理するようにします。  ユーザーが複数のテキスト範囲を指定することができます。  またVSPackage ではこの機能自体を制御できます。  どちらの場合も開いているすべてのドキュメントの現在のターゲットとターゲットのシェルに通知する必要があります。  
  
### 検索または置換を実行します。  
  
1.  フレームのプロパティ <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> または <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> によって返されるオブジェクトの 1 種類の <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>インターフェイスを実装します。  カスタム エディターを作成する場合はカスタム エディター クラスの一部としてこのインターフェイスを実装します。  
  
2.  テキスト エディターのサポートのイメージ検索を実行するかどうかを示します。オプションを指定するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> のメソッドを使用します。  
  
     エディターのサポートを検索するイメージをショートサーキット メッセージを送信 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> を実行します。  
  
     それ以外の場合は実装の <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>。  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> のメソッドを実装する場合<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> のインターフェイスを呼び出すことで取得タスクを簡略化できます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>