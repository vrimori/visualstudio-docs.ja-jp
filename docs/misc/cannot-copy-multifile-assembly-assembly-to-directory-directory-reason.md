---
title: "Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt;
複数ファイルのアセンブリは、実行起点となるプロジェクト ディレクトリのサブディレクトリにコピーされます。  たとえば、出力パスが "c:\\project1\\bin" のとき、そこにファイル a.dll および b.dll が格納されている Test という名前のアセンブリ \(`CopyLocal` プロパティは `true`\) が存在する場合、コピーが完了するとファイル構造は次のようになります。  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 このエラーは、"c:\\project1\\bin\\Test" をディスクに作成できなかった場合に、プロジェクト システムによって表示されます。  
  
 このエラーは、ディスク容量が不足しているか、パスの長さが MAX\_PATH の制限に達していることを示します。  
  
 **このエラーを解決するには**  
  
-   ディスク容量を確認してください。  
  
-   現在プロジェクトが置かれているフォルダーのパスよりもパスの長さが短いフォルダーに、プロジェクトを移動します。  
  
-   クライアント プロジェクトの場合は、絶対パスの長さが短いフォルダーに、出力ディレクトリを変更します。  
  
## 参照  
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)   
 [方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ja-jp/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)