---
title: アクセスが拒否されました |Microsoft Docs
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
ms.openlocfilehash: 9b49f60395a853d7dfda91738ccccaba9d585b46
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349479"
---
# <a name="access-is-denied"></a>アクセスが拒否されました
スクリプトは、現在のページのホスト以外のソースから、データにアクセスしようとしました。 Internet Explorer や他のブラウザーが従う同一生成元ポリシーは、現在のページの URL と同じスキーム、ホスト、およびポートのソースからのみ、スクリプトがデータにアクセスすることを許可しています。  
  
 たとえば、現在のページが`https://employees.mycompany.com`、次の Url からデータにアクセスすることはできません。  
  
-   `http://data.contoso.com`、HTTPS ではなく HTTP を使用しているためです。  
  
-   `https://somedatasource.com`を別のドメインであります。  
  
-   `https://employees.mycompany.com:8888`を別のポートを使用しているためです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   呼び出そうとしている API が、クロス オリジンのスクリプトを安全に許可する 2 つの手段である、JSONP または CORS をサポートしているかどうかを調査します。  
  
-   REST API を呼び出そうとしている場合は、サーバー側コードにこの呼び出しをリファクタリングして、クライアント側スクリプトの新しい REST エンドポイントを公開します。  
  
     詳しくは、同一生成元ポリシー、JSONP、および CORS に関連したオンライン ドキュメントを参照してください。
