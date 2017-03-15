---
title: "例外のトラブルシューティング : System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOException クラス"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IO.IOException
<xref:System.IO.IOException> は、ファイルの読み取りまたは書き込みに失敗した場合など、I\/O エラーが発生するとスローされます。  
  
## 関連するヒント  
 **ファイルとディレクトリが存在することを確認します。**  
 読み取り\/書き込みを実行する対象のディレクトリが存在することを確認します。 読み取ろうとしているファイルが存在することを確認します。  
  
### コメント  
 <xref:System.IO.IOException> は、ストリーム、ファイル、およびディレクトリを使用して情報にアクセスしているときにスローされる例外の基底クラスです。  
  
 基底クラス ライブラリには次の型が含まれます。これらは、<xref:System.IO.IOException> の派生クラスです。  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## 参照  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD 方法: CLR コンソール アプリケーションを作成する](http://msdn.microsoft.com/ja-jp/b8af4197-e65f-4b17-b18e-b9e92965d026)