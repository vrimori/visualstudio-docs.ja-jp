---
title: "Could not create output directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not create output directory &#39;directory&#39;. &lt;reason&gt;
プロジェクト システムがプロジェクト ディレクトリを作成できませんでした。  
  
 プロジェクト システムは、プロジェクトが開かれると同時にすべての出力ディレクトリを作成します。  プロジェクト システムによって作成される出力ディレクトリの一覧を次に示します。  
  
 *projectfolder*\\obj\\`configname`  
 構成に固有の一時的な出力ディレクトリ。  
  
 *projectfolder*\\obj\\`configname`\\temp  
 コンパイラによって使用される作業領域。  
  
 *projectfolder*\\obj\\`configname`\\temppe  
 デザイン時にデザイナーが使用する一時的なアセンブリが作成される場所。  
  
 outputdir  
 \[OutputPath\] プロパティによって設定するユーザー定義のアイコンです。  詳細については、「[\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)」を参照してください。  
  
 obj フォルダーの下にディレクトリが作成できない場合、最も一般的な原因として、ディレクトリ名が MAX\_PATH の制限を超えていることが考えられます。  
  
 それほど一般的な原因ではありませんが、アクセス許可が拒否されたり、ディスク容量が不足したりしている場合もあります。  
  
 **このエラーを解決するには**  
  
-   プロジェクトの場所を移動するか、プロジェクト構成の名前を短くします。  
  
     このエラーが発生した場合、ビルド プロセスは失敗します。  
  
## 参照  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)