---
title: "Could not bind to dependency &#39;assembly&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not bind to dependency &#39;assembly&#39;
プロジェクトのいずれかの参照自体に、格納はされているが無効なアセンブリの参照 \(依存関係\) が含まれています。  このエラーがプロジェクトのビルドを妨げることはありません。  ただし、実行時エラーが発生する場合があります。  
  
 この状況は、次の 3 つの条件がすべて当てはまることを示唆しています。  
  
-   ディスク上に同じ名前を持つ 1 つ以上のファイルが存在する。  
  
-   いずれかのファイルがアセンブリではない。  
  
-   参照のパスが、アセンブリ以外のファイルを格納するディレクトリを最初に検索している。  
  
 **このエラーを解決するには**  
  
-   プロジェクトが参照を検索するディレクトリの順序を変更します。  詳細については、「[NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/8e549b39-7256-456a-8fd7-089b23facf9c)」を参照してください。  
  
## 参照  
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)   
 [方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ja-jp/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)