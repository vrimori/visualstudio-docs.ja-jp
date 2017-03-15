---
title: "スクリプト デバッグの制約 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASPX ブレークポイント マップ, 制限事項"
  - "ブレークポイント マップ, 制限事項"
  - "スクリプトのデバッグ, 制限事項"
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# スクリプト デバッグの制約
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、クライアント側のスクリプトのデバッグをサポートしています。ただし、このトピックで説明する制約があります。  
  
## クライアント側スクリプトへのブレークポイントのマップでの制約  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、サーバー側の ASPX または HTML ファイルで、実行時にクライアント側ファイルに変換されるファイルの中にブレークポイントを設定できます。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、ブレークポイントをサーバー側ファイルからクライアント側ファイルの中の対応するブレークポイントにマップします。ただし、次の制限があります。  
  
-   ブレークポイントは `<script>` ブロック内に設定する必要があります。  インライン スクリプト内または `<% %>` ブロック内のブレークポイントは、マップされません。  
  
-   ページのブラウザー URL には、ページ名が含まれている必要があります。  たとえば、http:\/\/microsoft.com\/default.apsx です。  ブレークポイントのマップでは、http:\/\/microsoft.com などのアドレスから既定のページへのリダイレクトは認識されません。  
  
-   ブレークポイントは、ブラウザー URL で指定されているページ内に設定されている必要があります。そのページに含まれる ASPX コントロール \(ascx\) ファイル、マスター ページ、またはその他のファイルに設定されているブレークポイントはマップされません。  含まれるページに設定されているブレークポイントは、マップされません。  
  
-   `<script defer=true>` ブロック内に設定されているブレークポイントは、マップされません。  
  
-   `<script id="">` ブロック内に設定されているブレークポイントに対して、ブレークポイントのマップでは、`id` 属性は無視されます。  
  
## ブレークポイントのマップおよび重複行  
 サーバー側スクリプトとクライアント側スクリプトの対応する場所を検索するために、ブレークポイントのマップのアルゴリズムでは、各行のコードを調べます。  アルゴリズムでは、各行が一意であることを前提にしています。  2 つ以上の行に同じコードが含まれ、その重複行の 1 つにブレークポイントが設定されている場合、ブレークポイントのマップのアルゴリズムで、クライアント側ファイルの正しくない重複行が選択されることがあります。  この問題を回避するには、ブレークポイントを設定した行にコメントを追加します。  次に例を示します。  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```