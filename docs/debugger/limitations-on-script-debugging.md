---
title: スクリプトのデバッグに関する制限事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2b959428d940fd61c9c343f468fca71d56332c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="limitations-on-script-debugging"></a>スクリプト デバッグの制約
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、クライアント側のスクリプトのデバッグをサポートしています。ただし、このトピックで説明する制約があります。  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>クライアント側スクリプトへのブレークポイントのマップでの制約  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、サーバー側の ASPX または HTML ファイルで、実行時にクライアント側ファイルに変換されるファイルの中にブレークポイントを設定できます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、ブレークポイントをサーバー側ファイルからクライアント側ファイルの中の対応するブレークポイントにマップします。ただし、次の制限があります。  
  
-   ブレークポイントは `<script>` ブロック内に設定する必要があります。 インライン スクリプト内または `<% %>` ブロック内のブレークポイントは、マップされません。  
  
-   ページのブラウザー URL には、ページ名が含まれている必要があります。 たとえば、http://microsoft.com/default.apsx のようにします。 ブレークポイントのマップでは、アドレスからのリダイレクトをなど、認識できないhttp://microsoft.com既定のページにします。  
  
-   ブレークポイントは、ブラウザー URL で指定されているページ内に設定されている必要があります。そのページに含まれる ASPX コントロール (ascx) ファイル、マスター ページ、またはその他のファイルに設定されているブレークポイントはマップされません。 含まれるページに設定されているブレークポイントは、マップされません。  
  
-   `<script defer=true>` ブロック内に設定されているブレークポイントは、マップされません。  
  
-   `<script id="">` ブロック内に設定されているブレークポイントに対して、ブレークポイントのマップでは、`id` 属性は無視されます。  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>ブレークポイントのマップおよび重複行  
 サーバー側スクリプトとクライアント側スクリプトの対応する場所を検索するために、ブレークポイントのマップのアルゴリズムでは、各行のコードを調べます。 アルゴリズムでは、各行が一意であることを前提にしています。 2 つ以上の行に同じコードが含まれ、その重複行の 1 つにブレークポイントが設定されている場合、ブレークポイントのマップのアルゴリズムで、クライアント側ファイルの正しくない重複行が選択されることがあります。 この問題を回避するには、ブレークポイントを設定した行にコメントを追加します。 例えば:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```