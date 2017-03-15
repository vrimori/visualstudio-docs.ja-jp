---
title: "Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt;
.licx ファイルをバイナリのリソースに変換するために使用されるライセンス プロセッサが、何らかの原因で失敗しました。  
  
 一般に、このエラーは、無効な .licx ファイルが原因で発生します。  たとえば、このファイルがテキスト エディターで開かれ、変更を加えられている可能性があります。  
  
 このエラーが発生した場合、ビルド プロセスは失敗します。  
  
### このエラーを解決するには  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[すべてのファイルを表示\]** をクリックします。  
  
3.  ソリューション エクスプローラーで obj フォルダーを展開し、**Debug** フォルダーを展開します。  
  
4.  "myApplication.exe.licenses" という名前のファイルを検索します。myApplication はお使いの Windows フォーム アプリケーションの名前です。  
  
5.  このファイルを削除し、ソリューションを再ビルドします。  
  
## 参照  
 [方法 : コンポーネントおよびコントロールのライセンス処理を行う](../Topic/How%20to:%20License%20Components%20and%20Controls.md)