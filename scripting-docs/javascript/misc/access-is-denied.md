---
title: アクセスが拒否されました |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9c097cd09712d19acf5a0e4999b5c7a47469f958
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632732"
---
# <a name="access-is-denied"></a>アクセスが拒否されました
スクリプトは、現在のページのホスト以外のソースから、データにアクセスしようとしました。 Internet Explorer や他のブラウザーが従う同一生成元ポリシーは、現在のページの URL と同じスキーム、ホスト、およびポートのソースからのみ、スクリプトがデータにアクセスすることを許可しています。  
  
 たとえば、現在のページが https://employees.mycompany.com の場合、以下の URL からデータにアクセスすることはできません。  
  
-   http://data.contoso.com 、HTTPS ではなく HTTP を使用しているためです。  
  
-   https://somedatasource.com 、別のドメインになっているためです。  
  
-   https://employees.mycompany.com:8888 、別のポートを使用しているためです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   呼び出そうとしている API が、クロス オリジンのスクリプトを安全に許可する 2 つの手段である、JSONP または CORS をサポートしているかどうかを調査します。  
  
-   REST API を呼び出そうとしている場合は、サーバー側コードにこの呼び出しをリファクタリングして、クライアント側スクリプトの新しい REST エンドポイントを公開します。  
  
     詳しくは、同一生成元ポリシー、JSONP、および CORS に関連したオンライン ドキュメントを参照してください。