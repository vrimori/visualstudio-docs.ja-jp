---
title: 関数は、有効なプロトタイプ オブジェクトがありません |Microsoft ドキュメント
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633012"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>関数には、有効なプロトタイプ オブジェクトが存在しません。
使用しようとしています**instanceof**オブジェクトは、特定の関数クラスから派生しましたが、オブジェクトの再定義する場合を決定する`prototype`プロパティをいずれかとして`null`、または外部のオブジェクトの種類 (両方無効。[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクト)。 外部オブジェクトには、ホスト オブジェクト モデル (たとえば、Internet Explorer のドキュメントまたはウィンドウ オブジェクト) からオブジェクトまたは外部の COM オブジェクトを指定できます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   関数のことを確認`prototype`プロパティは、有効な参照[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [prototype プロパティ (Object)](../../javascript/reference/prototype-property-object-javascript.md)