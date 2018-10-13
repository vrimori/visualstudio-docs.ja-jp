---
title: スクリプトのデバッグに関する制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f597cad06870f23b7481f0375c9eb3abb550e4e1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251111"
---
# <a name="limitations-on-script-debugging"></a>スクリプト デバッグの制約
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] は、クライアント側のスクリプトのデバッグをサポートしています。ただし、このトピックで説明する制約があります。  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>クライアント側スクリプトへのブレークポイントのマップでの制約  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、サーバー側の ASPX または HTML ファイルで、実行時にクライアント側ファイルに変換されるファイルの中にブレークポイントを設定できます。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] は、ブレークポイントをサーバー側ファイルからクライアント側ファイルの中の対応するブレークポイントにマップします。ただし、次の制限があります。  
  
-   ブレークポイントは `<script>` ブロック内に設定する必要があります。 インライン スクリプト内または `<% %>` ブロック内のブレークポイントは、マップされません。  
  
-   ページのブラウザー URL には、ページ名が含まれている必要があります。 たとえば、 http://microsoft.com/default.apsx のようにします。 ブレークポイントのマップなどでアドレスからのリダイレクトを認識できない http://microsoft.com 既定のページにします。  
  
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



